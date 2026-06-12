---
title: "Lenovo SL510 suspend (S3 sleep) is not working"
date: 2010-01-26
forum: Hardware
---

### Post by kubik007 on 2010-01-26
Hi all,

I bought a new Lenovo SL510 with T5870 2GHz CPU, 250GB HDD, no OS, (part No. NSLQ7MC). Installation was without any problems, but** I didn't get the suspend working**. Hibernation works fine. 

When I click sleep button (or echo -n mem > /sys/pover/state), the screen backlight goes off, but windows on LCD are stil visible, after 10s fan goes to max and sleep LED is blinking wild. No further reaction to power button, I suppose the sleep routine hangs forever.

btw. I also tried with 32bit Suse Live CD, BIOS upgrade and 2.6.32 kernel, with the same result.

Did someone get the sleep mode working on SL510? 
Do you have 32 or 64bit? 
What is your hardware model? 

Many thanks for your help, regards Petr

---

### Post by Veinos on 2010-02-05
Hey, i have same model, with slightly different stats, and i can't have the sleep function working either... i tried couple things, but i'm new to linux in general.
Sleep does work in windows 7 and hibernation is working under linux and windows too
I'm using Linux mint 64, and tried default ubuntu 64 too with same result.

---

### Post by giannis1_86 on 2010-03-06
I have the same problem with you with same model.
The laptop suspends on black screen and doesn't want to resume whatever button i push.
Any help guys?

---

### Post by Veinos on 2010-03-29
anyone managed to solve this?

---

### Post by AlexKpow on 2010-05-19
If you press fn+f4 to sleep, then press it again to wake up (I have an SL510 as well). In System>prefs>power management I set it to suspend when laptop lid is closed and it works fine for me.

---

### Post by Veinos on 2010-05-22
what version of ubuntu are you using? and what video card do you have in your sl510 (if there's any options on that choice?)
Did it work right off the box?

---

### Post by AlexKpow on 2010-05-22
> **Veinos said:**
> what version of ubuntu are you using? and what video card do you have in your sl510 (if there's any options on that choice?)
Did it work right off the box?

Yes, I have the basic 4500 gpu thing, I'm using 10.04.

---

### Post by kubik007 on 2010-06-28
> **AlexKpow said:**
> Yes, I have the basic 4500 gpu thing, I'm using 10.04.

What is the CPU type (or GHz), please? 
I still didn't found any solution to the sleep problem. When I try what you describe, it stays with monitor on and max fan. I have seen my model (T5870 @ 2.0GHz) is not sold any more, maybe for later models this works fine.

---

### Post by finlost on 2010-06-30
Sorry for the slight threadjack...

I currently run a dual boot Lenovo IdeaPad Y510.  The hinge for the cover to open and close the screen has sheet the bed on me.  The laptop works fine, but I know someday the screen is going to die and buh-bye to easily retrieving my important files.

I am looking at a few different ThinkPad SL510 configurations.  Save the sleep issues, is the SL510 a good dual boot machine?  I would probably go 64-bit.

---

### Post by Veinos on 2010-10-07
What version of ubuntu did you try btw?? the 32 bit or 64? if that can have any difference?

---

