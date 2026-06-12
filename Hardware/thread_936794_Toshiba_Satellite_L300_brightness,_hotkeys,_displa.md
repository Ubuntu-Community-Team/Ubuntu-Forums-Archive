---
title: "Toshiba Satellite L300 brightness, hotkeys, display options"
date: 2008-10-03
forum: Hardware
---

### Post by jabadabuntu on 2008-10-03
Hi everybody,

i have the following problem:

i use a toshiba satellite L300 and installed hardy heron on it. I'm trying to find a way to push down the brightness of my display. I couldn't find any interface where i can do this. The hotkeys of my laptop (i.e. Fn + F6) don't work. I have found out that there is a special toshiba acpi driver which should fix this problem. From [http://memebeam.org/toys/ToshibaAcpiDriver]("http://memebeam.org/toys/ToshibaAcpiDriver") i downloaded the appropriate patch file but when i execute the patch in the terminal i get the following error:

```
ichbin@ichbin-laptop:~$ patch -p1 < toshiba_acpi-dev_toshiba_test5-linux_2.6.21.patch
missing header for unified diff at line 3 of patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- toshiba_acpi.c.21.orig	2007-04-28 00:49:26.000000000 +0300
|+++ toshiba_acpi.c	2007-05-15 19:23:32.000000000 +0300
--------------------------
File to patch: toshiba_acpi-dev_toshiba_test5-linux_2.6.21.patch
patching file toshiba_acpi-dev_toshiba_test5-linux_2.6.21.patch
Hunk #1 FAILED at 28.
Hunk #2 FAILED at 55.
Hunk #3 FAILED at 507.
Hunk #4 FAILED at 738.
Hunk #5 FAILED at 747.
Hunk #6 FAILED at 764.
6 out of 6 hunks FAILED -- saving rejects to file toshiba_acpi-dev_toshiba_test5-linux_2.6.21.patch.rej
```

Do i do something wrong in the execution command?
Is there another way to cutomize display settings, e.g. through terminal commands? (manipulating the gamma with the xgamma command doesn't help me
i need to push brightness and contrast down)


thanks in advance
jabadabuntu

---

### Post by sergiom99 on 2008-10-03
there are several threads here (even in the last couple of days) about "screen brightness" use those keywords.
You can try xbacklight in console.

Also, I think I've seen something in Synaptics (or Adept package manager) for toshiba laptop hotkeys. Search there for toshiba.

---

### Post by jabadabuntu on 2008-10-04
Hi sergiom99,

thanks a lot for your reply. The xbacklight package is a good solution for the moment. 

Is there a way to make my own hotkeys in ubuntu? E.g. I would make some key combination which executes the xbacklight command. I think somewhere i have read something like this.

Apart from this: if there is someone who can handle such "patch-errors" like "Hunk #1 FAILED at 28." please reply.


jabadabuntu

---

### Post by sergiom99 on 2008-10-05
keytouch lets you define your own keyboard layout. and there should be some way to bind some keys to special actions but i am not sure how.
fnfxd is a package to manage hotkeys for toshiba laptops.

---

### Post by jabadabuntu on 2008-10-11
i haven't tried keytouch yet but to get the fnfxd package to run i need to install a special toshiba acpi driver i have mentioned above. this leads to the problem with the patch file again. vicious circle :?

---

### Post by Hachi-Roku on 2009-02-16
i posted this in another thread similar. ive got the same laptop. I did a right click on taskbar and "add to panel" a brightness adjuster. works great and settings are remembered!

---

### Post by frito_x on 2009-05-23
> **Hachi-Roku said:**
> i posted this in another thread similar. ive got the same laptop. I did a right click on taskbar and "add to panel" a brightness adjuster. works great and settings are remembered!
heh... so close it almost bit me... thanks... much better solution than xbacklight.

---

### Post by san007 on 2009-06-06
[B]Hello........

               I was also suffering from this problem of brightness adjustment[/B].......
fn+F6  was not working............

to solve this problem  you have to 2 driver........

[B][I]1.. SL300_XP_TOSHIBA_Common_Modules
2...SL300_XP_TOSHIBA_Hotkey_Utility........[/I][/B]

First install common_module driver   and then  Hotkey_utility driver.......and its done....

If u have any problem regarding this or want these driver mail me: **san_kumar_sharma@yahoo.co.in**........................

;)

---

### Post by rocdoc on 2011-01-29
I just solved many of the Function Key and fan control problems with my L300 - read this:

[https://wiki.archlinux.org/index.php/Toshiba_Satellite_L300](https://wiki.archlinux.org/index.php/Toshiba_Satellite_L300)

---

### Post by ezed on 2012-02-04
hi, i was able to solved it.
i can't remember where but in one of the threads said that the solution was to upgrade the bios. I've done and it finally worked out, with Fn keys also.
And health for your eyes at last! Un abrazo!

pd.
In case it is necessary, here i write the instructions:
download from toshiba web site the latest bios, it's an .exe file.
inside that .exe, see in the readme file if it is compatible with your laptop, i guess it will be, or just run the .iso file
boot from cd

---

### Post by overdrank on 2012-02-04
Back to sleep thread. Thread closed.

---

