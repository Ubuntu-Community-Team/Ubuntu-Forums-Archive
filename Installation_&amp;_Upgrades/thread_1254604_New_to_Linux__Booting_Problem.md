---
title: "New to Linux | Booting Problem"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by ni_shi2005 on 2009-08-31
Hi guys!! i am noob just steped into the open souce world! i installed Ubuntu 9.04!! but i messed up with the partitions! allocated to much space for / dirctry! and less for the home dirctry!! now i have to reinstall the OS n do the partition correctly again!!
but the problem is i cant boot from the CD which i used to install the windows today morning! 
before starting OS it says press [esc] to go to menu or somthing!
if i pressed ESC i am given 4 options like 
Ubuntun bla bla Generic .11 
Ubuntun bla bla Generic .11 [recovery] 
Ubuntun bla bla Generic .15 
Ubuntun bla bla Generic .15 [recovery]
 
none of the option leads me to the installation process!!
please help me with this problem!!!
 
note i hav checked BIOS settings n all....not working with this!

---

### Post by holycow131415 on 2009-08-31
tell your bios to not boot from the harddrive at all and only the CD or hit f12 for boot menu. what you were seeing is the grub menu, which is on the only harddrive, i believe.

---

### Post by jerrrys on 2009-08-31
the CD will no do this (boot to OS).  you must be booting your HDD.  to prove this, boot up without cd and see if it boots.  if so, you probably need to set boot from cd in your BIOS...

---

### Post by ni_shi2005 on 2009-08-31
guyz i have set da CD rom as da 1st in priorites in BIOS settings!! and when the machine waz in windows i booted with the same seetings with da same CD!! is there anyOther way to install!! like shell prompt or somthing?

---

### Post by ni_shi2005 on 2009-08-31
> **jerrrys said:**
> the CD will no do this (boot to OS). you must be booting your HDD. to prove this, boot up without cd and see if it boots. if so, you probably need to set boot from cd in your BIOS...
 
you are corrct i tried without the CD same thing happens..it means da CD is not booting!!!
now wot to do? da BIOS setting is Correct!! :confused:

---

### Post by ni_shi2005 on 2009-08-31
i am waitin for help :(

---

### Post by jerrrys on 2009-08-31
if settings were correct you would be booting from cd.  an idea, in BIOS you have it set to boot from CD.  also in BIOS, there should be an option to turn off boot from HDD

---

### Post by ni_shi2005 on 2009-08-31
where is it!! i cudnt find it :(

---

### Post by jerrrys on 2009-08-31
not sure if your box has that option, what kind of a system/model do you have?

---

### Post by tal007 on 2009-08-31
Before your system gets  to those horrible messages bring up the system BIOS menu. In your CMOS setting check the  boot order. Also, see if your BIOS can see your CDROM drive. Sometimes things get messed up during installation. 

Boot order:

             1]  Floppy         [ on / off / auto detect ]
             2]  CD/DVD      [ on  / off / auto detect ]
             3]  Hard Drive   [ on / off /auto detect  ]

Again, your BIOS may not be same as mine, but nonetheless you might have something similar to  this in your BIOS. Change your CD to auto detect. Keep in mind, the order in which you set these also important. You must set it to either 1 or 2, then  "SAVE" it in your CMOS. Then give a try.

---

### Post by ni_shi2005 on 2009-08-31
Mission Failed!! coz i dont have dat kinda BIOS system!! its a ****!! jst can giv an order :(

---

### Post by tal007 on 2009-08-31
This may be a very simplistic answer to a complex problem, but none the less it happens. Sometimes I open my case, connect and disconnect drives and in the process end up leaving something loose. I hope it is not that kind of a problem.

---

