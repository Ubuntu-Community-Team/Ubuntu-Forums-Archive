---
title: "Trouble with graphics lag in Ubuntu 14.04 | AMD Graphics Card"
date: 2014-05-20
forum: Hardware
---

### Post by rahuldsouza on 2014-05-20
I'm really puzzled by what is going on. Ever since I installed 14.04 I've been having some terrible problems with graphics, or at least what I think is a graphics problem. I've looked everywhere and have not come across a solution, of course, I've only looked for it as a graphics problem. Let me break down all the issues at hand.

The problems:

1. After loading and after a period of time, the pointer leaves several ghosts across the screen when moved. 
2. Switching between tabs in any program often leads to the new tab only being revealed after I drag the pointer over various parts of the window.
3. Whenever I open a menu, the menu highlight slowly appears and dissapears around the pointer.
4. Typing and deletion doesn't always translate to quick action on the screen (this is not too bad and happens sparingly). 

The result of my lspci | grep VGA is
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]

I really hope someone here can solve this problem for me. Let me know if there is any more information that you need to help me diagnose the problem, Thank you for reading this!

Edit: Forgot to mention, I did install xubuntu-desktop in order to see if the problem persists in that environment and it was much of the same. In fact the problem with the ghost pointers wouldn't go away.

---

