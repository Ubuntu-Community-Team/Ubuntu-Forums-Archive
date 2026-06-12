---
title: "Dell Vostro with HD4000/Radeon HD 7670M. X Server fails to start"
date: 2013-06-20
forum: Hardware
---

### Post by andrewmchugh on 2013-06-20
OS - xubuntu 13.04 64bit fresh install (up to date)


I'm trying to install the ati/amd graphics drivers for the laptops dedicated graphics card, but im having a really hard time.


So I freshly installed xubuntu and then followed the [instructions]("http://ubuntuforums.org/printthread.php?t=1930450&pp=75") for switchable graphics from this forum. 


After I did the first `sudo aticonfig --initial -f` and rebooted it just sits on a backscreen with cursor (_) flashing in the top left. I switched to tty1 and tried```
 sudo startx
``` then X server failed to start because it couldn't find a screen. 

Is there anything else I need to do that's not included on those instructions? 

ALSO. I reinstalling xubuntu and tried just installing the amd drivers alone as per the instructions on [here]("http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide").

So I have used the ati driver with aticonfig.. that says it can't find the adapter. And I have tried amdconfig which finds the adapter (doesn't get the same error as aticonfig did) but black screens on start up. If I set a black xorg.conf I will  
boot but will be just like a fresh install default driver.

(I'm a programmer/ CS game eng student) but not all that familiar with Xorg.

Laptop : [Dell Vostro 3560]("http://www.dell.com/uk/business/p/vostro-3560/pd?oc=sbn35638&model_id=vostro-3560"), i7-3632QM, AMD Radeon HD 7670M 1GB

---

### Post by andrewmchugh on 2013-06-21
Today I installed Ubuntu 12.04 LTS and tried the same again .. results were the same :(

---

### Post by kike2 on 2013-08-01
I'm having the same problem, but the characteristics are a little bit different:

Laptop: Dell Vostro 3560, i7-3612QM, AMD Radeon HD 7600M series of 1GB.

After install Ubuntu 12.04 LTS apparently was no problem, but the system did not recognize the Graphics Card, the fan was always on.
Therefore the battery discharged in less than an hour. 

I tried to reboot and I got this message: "Can't find 0xX in attribute list".

Now I can not use Ubuntu, if there is a way please let us now it. How you can see I'm not an expert using Linux.

Thanks for your time and comments.

---

### Post by kike2 on 2013-08-01
Not sure if this detail is useful: I installed Ubuntu in a dual mode with Windows 7

Best regards.

---

### Post by Bashing-om on 2013-08-01
kike2 & andrewmchugh;

Does the "M" in HD 7600M series denote swithable graphics, as in also having integrated Intel chip ?

Let's look at what you have onboard; post the output of terminal codes:
```

lspci | grep VGA
lspci -nnk | grep -iA3 vga

```

 If you see more than one graphics card, then you have a switchable graphics setup.
Check if both the cards are powered on:
To check this, we need be able to view the file /sys/kernel/debug/vgaswitcheroo/switch. Type the following in terminal.
```
cat /sys/kernel/debug/vgaswitcheroo/switch
```
One driver per card per instance, else the kernel is all confused and chaos results.
The kernel needs a bit of guidance.

Depending on what is, is the follow up advise.

---

