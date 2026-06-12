---
title: "Newbie Install Problem SAGEMATH"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by peter_kint on 2009-08-29
[SIZE=2]Hi,
I downloaded the binary **sage-4.1.1-linux-Ubuntu_9.04-i686-Linux** and extracted it to my desktop, from where -according to SAGEMATH([http://www.sagemath.org)-]("http://www.sagemath.org%29-") I should be able to run the program from a terminal by the command **./sage**

This is what I get:
[/SIZE][INDENT][FONT=Arial][SIZE=2]peter@peter-desktop:~$ cd Desktop[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]peter@peter-desktop:~/Desktop$ cd sage-4.1.1-linux-Ubuntu_9.04-i686-Linux[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]peter@peter-desktop:~/Desktop/sage-4.1.1-linux-Ubuntu_9.04-i686-Linux$ ./sage[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]----------------------------------------------------------------------[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]| Sage Version 4.1.1, Release Date: 2009-08-14                       |[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]| Type notebook() for the GUI, and license() for information.        |[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]----------------------------------------------------------------------[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]The Sage install tree may have moved.[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]Regenerating Python.pyo and .pyc files that hardcode the install PATH[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2](please wait at most a few minutes)...[/SIZE][/FONT][SIZE=2]
**[FONT=Arial]Do not interrupt this.[/FONT]**
[/SIZE][FONT=Arial][SIZE=2]sage:  [/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]sage: [/SIZE][/FONT][SIZE=2]
[/SIZE][/INDENT][SIZE=2]**What does he want now? **Seems pretty frightening (He warns me not to close the terminal...)
[/SIZE]

---

### Post by Fox5 on 2009-10-03
If it gives you the sage prompt, it's probably finished whatever it was doing. You should be free to type notebook() and get the GUI interface.

I had difficulty running the binary on the Karmic Koala beta though, I ended up having to compile from source on my Pentium M laptop, a process that took about 8 hours.

---

