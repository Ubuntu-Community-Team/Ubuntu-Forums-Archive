---
title: "[SOLVED] A little C advice, please"
date: 2008-09-27
forum: General Help
---

### Post by Arkeides on 2008-09-27
This issue concerns C.

I'm trying to teach myself C, and after learning about constants, decided to test my knowledge by creating a simple program to calculate the value a 15% gratuity. This is my program listing:

   1:	//A program to calculate the 15% gratuity normally used for tipping
   2:	#include <stdio.h>
   3:	
   4:	const float STANDARD_TIP = .15;
   5:	float price;
   6:	float tip;
   7:	
   8:	int main (void)
   9:	{
  10:	   //Get the amount of the bill
  11:	   printf("Enter the amount of the bill: ");
  12:	   scanf("%d", &price);
  13:	
  14:	   //Performs the calculation
  15:	   tip = STANDARD_TIP * price;
  16:	
  17:	   //Displays the tip
  18:	   printf("\nYou should leave: %d \n", tip);
  19:	
  20:	   //Troubleshooting
  21:	   printf("\nThe value of STANDARD_TIP is: %d", STANDARD_TIP);
  22:	   printf("\nThe price of the meal is: %d", price);
  23:	   printf("\nThe tip was calculated to be: %d\n", tip);
  24:	
  25:	   return 0;
  26:	}

  
The problem is, the value keeps coming out to zero. To try and troubleshoot, I added lines 20 - 23. STANDARD_TIP displayed a ridiculously large value, 1073741824. I ran the program with the price of 23.41, though if I'm using STANDARD_TIP as a constant, I don't think user input should affect it. I've tried the following as well:
#define STANDARD_TIP .15 as well as
#define STANDARD_TIP 0.15, but still, it doesn't keep that value.

Where am I going wrong, and if my code is sound, what might be up with my compiler? I'm using gcc.

Thank you,
Arkeides

---

### Post by mike2357 on 2008-09-27
I think that %d and floats don't mix well in printf and scanf.

Try %f, or for more precision, %.2f

---

### Post by Arkeides on 2008-09-27
Thanks, that worked. Now I've got output out to 6 digits of accuracy, but at least it's the right answer. I suppose later on in my lessons I'll learn the difference between %d and %f, but for now, it's enough to know to use %f for float. Thanks again.

---

### Post by John164918a on 2008-09-27
The first one on the list when you google "c++ stdio.h", this one here: [http://www.cplusplus.com/reference/clibrary/cstdio/](http://www.cplusplus.com/reference/clibrary/cstdio/) is crystal clear about all the functions in stdio.h like printf and scanf. That is what I use because I cant remember all the format descriptors

---

