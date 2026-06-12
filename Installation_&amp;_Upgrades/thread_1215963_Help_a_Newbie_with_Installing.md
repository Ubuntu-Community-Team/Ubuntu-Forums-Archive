---
title: "Help a Newbie with Installing"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by bbucsis on 2009-07-17
Hi There everyone, I'm brand new to the Ubuntu universe and am needing a bit of support with instaling Ubuntu to my Acer Aspire One netbook (standard specs with Intel Atom).

Ive downloaded the .IMG File and put it onto a USB stick using the Disk Imager supplied on the Install page. The next bit of instruction is asking me to run a Command Line Interface- I understand what the instructions ask me to do, however the website I am linked to for the file needed to run the Line is in Russian (I think?) and so I am having difficulty navigating it.

Just needing some help with this last bit of the process. Also, after I run the Command Line, will I simply need to repoot my Netbook for it to read as a boot disk, and then install Ubuntu from there? Also, does Ubuntu have an automatic partition manager while installing, or should I partition my drive before hand?

And last question, the Netbook came preinstalled with Windows XP, I have since installed several programs to this OS. I just want to make sure that when I install Ubuntu to my Netbook under a seperate partition that it will not remove any of these files or programs, and that they will be able to be run if I boot in Windows XP again in the future?

Thanks for helping me out, I know this is alot of questions, and I am sorry if any of this has been answered previously in the forums. I tried searching for answers, but I couldn't really find anything that helped me. Thanks in advance for the help!

---

### Post by neu2buntu on 2009-07-17
i used "unetbootin" to make a live usb to install ubuntu onto my aa1,.. and you will have the option of keeping windows and installing alongside it,so in other words a dual boot... although i did this from my other laptop running ubuntu i am almost sure it can be done from windows...... just search unetbootin on google

---

### Post by bbucsis on 2009-07-17
Ok, Ill definitely try using that program- just need to format the memory stick now so I can do it again.

Do you have any answers to my other questions?

---

### Post by neu2buntu on 2009-07-17
obviously you will have to free up space for the ubuntu install ,either in windows itself or booting up with the live usb and using gparted !!!    

well gladu scrapped that 1st part (especially when it is in russian).lol... > (1)Also, does Ubuntu have an automatic partition manager while installing, or should I partition my drive before hand?   yes it has a partitioner in the installer ,so no need to partition manually for the install.(as in / swap etc)

> (2)And last question, the Netbook came preinstalled with Windows XP, I have since installed several programs to this OS. I just want to make sure that when I install Ubuntu to my Netbook under a seperate partition that it will not remove any of these files or programs, and that they will be able to be run if I boot in Windows XP again in the future? you will have the option of keeping windows during the install,... just do a disk defrag and check disk for errors in xp before you install ubuntu and all should be well  

i have not dual booted in a long time myself so i hope i am fully accurate here, but the 1 thing im 100% on is using unetbootin for the install!!

---

### Post by bbucsis on 2009-07-17
Alright, Ive got the UNetbootin program and am trying to use it to install the IMG to my USB Drive, but every time I attempt to the program goes to Not Responding. I've tried this on two seperate computers with the same result, leaving the program for some time before deciding that it truly is frozen. Hopefully I am not doing something wrong...

---

### Post by bbucsis on 2009-07-17
Erk! Nevermind :P Turns out I just didn't wait long enough. Ok, crossing my fingers now!

---

### Post by neu2buntu on 2009-07-17
i used the .iso of ubuntu and used unetbootin to make the bootable usb,... im not sure if .IMG will work for this, hopefully it does!!! and unetbootin will show what is happening during the usb loading stage!!!!

---

### Post by bbucsis on 2009-07-17
OK, so the unetbootin does not like the .img file for the netbook version of Ubuntu. After a while of waiting it said it was finished, however when I tried to boot off of the USB it would get to an unusual loading page and stay there asking me to input a command. No command listed in the Help file would boot the OS so I rebooted in windows.

Then I did what Neu did, which is use the normal ISO for the 32 Bit Ubuntu. I formatted my memory stick, put the .iso file onto the memory stick with unetbootin, rebooted and booted with the memory stick, and it worked fine!

After previewing Ubuntu for a while on my netbook I installed it and am having no trouble at all. Thanks so much for all of your help. I hope this thread can help others in the future!

---

