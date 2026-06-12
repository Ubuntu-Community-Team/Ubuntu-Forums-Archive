---
title: "Sleep/Suspend when closing lid Ubuntu 9.10"
date: 2010-01-25
forum: Hardware
---

### Post by evanjohan on 2010-01-25
I installed Ubuntu 9.10 a few days ago and can not get it to suspend to ram when closing the lid. I've tried using the System>Preferences>Power Management to suspend but it doesn't do anything (under the AC Power tab or the Battery Power tab).  I can manually suspend to ram by checking the login name>Suspend in the upper right corner and it will suspend and resume without any issues.

I'm not an advanced user by an stretch of the imagination.

My laptop:
Toshiba Satellite L305D-S5934
Ubuntu 9.10 64-AMD
AMD Turion™ X2 Dual-Core Mobile Processor RM-70 
3GB PC6400 DDR2 800MHz SDRAM
ATI® Radeon™ 3100 

I'm sorry if this is a duplicate question, but I can't seem to find a fix (that I understand at least).

Thanks!

-Evan

---

### Post by llawwehttam on 2010-01-25
How do you know its not suspending to ram? I can't hear the fans in my laptop anyway so there is no difference in sound for me and as I have 4GB DDR3 Ram it wakes up from suspend in under 2 seconds.

---

### Post by evanjohan on 2010-01-25
I can see the screen is still on, can feel the fan, hear the harddrive spin and see that the wireless is still on since the led is on.

---

### Post by linux nut on 2010-01-25
How long are u waiting for it to fall asleep it takes a little while to respond when u close the lid

---

### Post by evanjohan on 2010-01-25
I've left it from 5-30 minutes with nothing.  When I was running Vista is would suspend with in 10 seconds.

---

### Post by neeraj2608 on 2010-01-25
> **evanjohan said:**
> I installed Ubuntu 9.10 a few days ago and can not get it to suspend to ram when closing the lid. I've tried using the System>Preferences>Power Management to suspend but it doesn't do anything (under the AC Power tab or the Battery Power tab).  I can manually suspend to ram by checking the login name>Suspend in the upper right corner and it will suspend and resume without any issues.

I'm not an advanced user by an stretch of the imagination.

My laptop:
Toshiba Satellite L305D-S5934
Ubuntu 9.10 64-AMD
AMD Turion™ X2 Dual-Core Mobile Processor RM-70 
3GB PC6400 DDR2 800MHz SDRAM
ATI® Radeon™ 3100 

I'm sorry if this is a duplicate question, but I can't seem to find a fix (that I understand at least).

Thanks!

-Evan
As I understand it, Gnome power manager does not handle power management in Karmic (that functionality has been moved to devicekit-power). The reason clicking the login name>suspend button works is that it directly calls the [FONT="Courier New"]pm-suspend[/FONT] command.
You could always write a script for the ACPI daemon to handle the lid close event. It's only a workaround, but it'll work.

---

### Post by evanjohan on 2010-01-25
Okay, but I'm not very familiar with coding and how I was start. Is there a place for dumbies and a walk through where I could learn to do this myself?

---

### Post by neeraj2608 on 2010-01-26
> **evanjohan said:**
> Okay, but I'm not very familiar with coding and how I was start. Is there a place for dumbies and a walk through where I could learn to do this myself?
These should help:
[LaptopSpecialKeys]("https://help.ubuntu.com/community/LaptopSpecialKeys")
[Suspend on lid close]("http://ubuntuforums.org/showpost.php?p=632569&postcount=2")

Let me know if you have any problems.

---

### Post by neeraj2608 on 2010-01-26
> **neeraj2608 said:**
> These should help:
[LaptopSpecialKeys]("https://help.ubuntu.com/community/LaptopSpecialKeys")
[Suspend on lid close]("http://ubuntuforums.org/showpost.php?p=632569&postcount=2")

Let me know if you have any problems.

I got some time to type out a solution.

First, make sure [FONT="Courier New"]pm-suspend[/FONT] runs on your system by typing the command [FONT="Courier New"]sudo pm-suspend[/FONT] in a terminal (from your OP, I'm sure it does but confirm anyway).

Next, navigate to directory /etc/acpi/events and create a new file (call it whatever you want) with the following content:
```
event=button/lid.*
action=/usr/sbin/pm-suspend
```
You'll need [FONT="Courier New"]su[/FONT] privileges to create this file, but you probably know that already. :)

Make sure [FONT="Courier New"]pm-suspend[/FONT] does not need a password when it is sudo'ed (by you). To do this, open up [FONT="Courier New"]/etc/sudoers[/FONT] (again, you'll need [FONT="Courier New"]su[/FONT] privileges) and add the following line at the end of the file (with the string [FONT="Courier New"]<your_user_name>[/FONT] replaced by your actual username, of course):
```
<your_user_name> ALL=NOPASSWD: /usr/sbin/pm-suspend
```

---

### Post by neeraj2608 on 2010-01-26
> **neeraj2608 said:**
> I got some time to type out a solution.

First, make sure [FONT="Courier New"]pm-suspend[/FONT] runs on your system by typing the command [FONT="Courier New"]sudo pm-suspend[/FONT] in a terminal (from your OP, I'm sure it does but confirm anyway).

Next, navigate to directory /etc/acpi/events and create a new file (call it whatever you want) with the following content:
```
event=button/lid.*
action=/usr/sbin/pm-suspend
```
You'll need [FONT="Courier New"]su[/FONT] privileges to create this file, but you probably know that already. :)

Make sure [FONT="Courier New"]pm-suspend[/FONT] does not need a password when it is sudo'ed (by you). To do this, open up [FONT="Courier New"]/etc/sudoers[/FONT] (again, you'll need [FONT="Courier New"]su[/FONT] privileges) and add the following line at the end of the file (with the string [FONT="Courier New"]<your_user_name>[/FONT] replaced by your actual username, of course):
```
<your_user_name> ALL=NOPASSWD: /usr/sbin/pm-suspend
```

Almost forgot to mention: you'll need to reboot to see if your changes work.

---

