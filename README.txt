
Code to refactor
=================
1) app/Http/Controllers/BookingController.php
2) app/Repository/BookingRepository.php

Code to write tests (optional)
=====================
3) App/Helpers/TeHelper.php method willExpireAt
4) App/Repository/UserRepository.php, method createOrUpdate


----------------------------
Note: this assement only contains examplary fixes for the approaches described here in the readme, the changes have not been deployed all over the code due to shortage of time as i was already running late from submissions time!

X. A readme with:   Your thoughts about the code. What makes it amazing code. Or what makes it ok code. Or what makes it terrible code. How would you have done it. Thoughts on formatting, structure, logic.. The more details that you can provide about the code (what's terrible about it or/and what is good about it) the easier for us to assess your coding style, mentality etc

Code OverView:
    First of all i had to attempt this in a very short time as i was on a trip and by the time i could read my email it was already the third day for test submission.
Excuses aside here are my thoughts on this code.

!!!! This is some terrible code! i say that due to below mentioned reasons:

1) I dont find any exception handling whatsoever in this code! this is the most terrible part of this code!

2) not only exception handling is missing (try catches etc.) there are many instances in the code where the conditions have been poorly managed which leaves obvious cases as un handled!
for example : many functions in the BookingRepository.php check for user through query and all the following conditions from there on check for if the user is found! but he case where the
user is not found is not managed properly! moreover if no operation can be performed without the user found in the respective functions why not just exit the function upon checking rather than run all the conditions unnecessarily.

3) There is no structure for responses set in the controller! response for each api contains data according to requirement but no internal status codes and messages have been managed for all of the functions other than 1 or 2.

4) Whenever making query from database the case if the record is not found has been ignored!

5) None of the functions in the controller or the repository have any kind of validations placed which allows malformed data to enter the process which in turn due to above mentioned points will return in 'Errores fatales' (fatal errors described in spanish to emphasize!)!

6) Too many conditional statements have been used rather than trying to manage the logics through other ways.

7) Some fields that obviously have defined values in the database have been managed through hard codding rather than setting up constants or enumerations for them!

8) request model binding has been used once or twice  which could have been used more.

9) last but not the least  The repository design pattern used could have been used in a better way where the functions could have been easy broken into db operations and placed in the repository layed and the flows should have been managed in the service layer which in tern should have been accessed by controller layer where upper level of flows should have been managed
for example an api has tp perform 2 operations from a single url the basic elements of those two processes should have been placed in the repository layer which should have been accessed by two separate service level functions for both operations and which in turn should be accessed by a single controller function that can be accessed thorugh the respesctive endpoint!   (seems tricky when explaining in written)


!!!! The code does have some positive approaches:

1) Repository design pattern has been implemented  some capacity.
2) Nomenclature for functions is mostly descriptive.
3) Eloquent has been used to good extent rather than switching to raw queries or excessive functions for ease.
4) The length of the functions has been kept mostly to the shorter side which is very good for readability.


===== expected output is a GitHub link with either =====

1. Readme described above (point X above) + refactored code 

Thank you!


