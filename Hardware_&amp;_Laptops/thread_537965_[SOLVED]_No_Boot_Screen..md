---
title: "[SOLVED] No Boot Screen."
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by diwas on 2007-08-29
well iam new to linux and ubuntu too. i have tried to search the problem i am havin in the forums...but couldnt get anything. if you can help me i'd be greatful.
my hardware configuration is:
512MB RAM
64MB graphics card(internal)
motherboard id : D845GVSR
processor: Pentium 4 1.8Ghz
Windows XP in the 1st partition
the problem iam  facing is that...after i select ubuntu to start in the GRUB bootloader...my screen goes pitch black..no boot screen and all...directly the log in screen appears after about 3-4minutes. but after ubuntu starts...everything goes fine...OS works very nicely.

please help me in this problem...i really want to learn linux.
please mail me the solution if u can...otherwise direct me to the place where i can get the help.

thank you.

---

### Post by ajgreeny on 2007-08-29
Next time you boot up, wait until the screen goes to balck for the few minutes and press Ctrl+Alt+F1.  This will take you to a command line boot and may give some answers to the question of what is happening (or not) at that time.  Report back any error messages that you see.

---

### Post by diwas on 2007-08-30
Thank you...but i think that there is some problem durin installation. Well it said to have some space as SWAP...since i had separated abt 10GB for ubuntu..i thought i didnt require any SWAP space...so i did not separate any space for SWAP...is it the reasonable cause for my problem?
And yeah i will try ur solution first.
And is my hardware requirement okay for ubuntu 7.04?

---

### Post by ajgreeny on 2007-08-30
How big are your partitions for winXP and ubuntu?  Swap is important but I don't think with 512 MB you would get a problem at boot time, though you might later in ram intensive operations like copying lots of photos from folder to folder.  The rest of your spec should be fine for ubuntu but it is always possible that the video card is not supported; you have not mentioned the name.

---

### Post by diwas on 2007-08-31
My graphics card is inbuilt intel's D845GVSR mother board's. I dont know much more about it.
Well for XP it is abt 13.3GBs and Ubuntu is 9 and 1GB swap. 
I tried ur way abt pressin Alt+Ctrl+F1...the message was "loadin please wait" ... and after sometime...the loadin comes (I mean the loadin which shows the mountin of CD drives and drivers...network and all stuffs...u got it ddnt u?) Then when its finished....login screen comes and then it works as usual...widout any problem.
I still wonder y my boot loadin screen doesnt come.

---

### Post by diwas on 2007-09-05
Anyone can help me?

---

### Post by diwas on 2007-11-20
Actually this problem is solved as i upgraded ubuntu version to 7.10...now i have a nice lookin boot screen and the OS loads fast too.

---

