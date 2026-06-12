---
title: "Ubuntu 9.04 won't boot without being plugged in HP dv6000"
date: 2009-04-25
forum: Hardware
---

### Post by travisgmyers on 2009-04-25
Hey, I've been using Ubuntu on a desktop for awhile now (still a noob though) and love it!  With the most recent release I finally got enough courage to stick it on my Laptop.  The installation when well for the most part.  I had a few small problems and was able to fix all but one.

My computer won't boot or shutdown unless its plugged in.  It runs fine doing everything else on battery though.  At first I thought maybe it was the battery because its older one, but I tried another battery that is practically new and has hardly been used and it still does the same thing.

Here is what happens:
When I try to boot without being plugged in, it flashes the HP logo and the options to enter the bios.  Then some text comes up on the top of the screen.  After that, the screen goes blank. (the power light is on but not the hdd light)

The instant I plug in the power cord, the Ubuntu logo comes up and it finishes booting.  After it boots, I can run everything fine without being plugged in.

Operating System: Ubuntu 9.04
Computer: HP Pavillion dv6000
Processor: AMD Athlon 64 X2 Dual-Core Processor TK-57 1900MHz
Memory: 2GB

I've checked around and can't seem to find any posts similar to this.  If there are, sorry I posted.  Any help is greatly appreciated! Thanks!

---

### Post by travisgmyers on 2009-04-26
Okay, weird update.  I noticed if I hold down a key (so far any random key) on the keyboard, it will boot without being plugged in. :lolflag:

Anyone have any ideas about that?

---

### Post by lusv on 2009-04-26
it happend to me too!

my notebook is a compaq presario f700...

during the boot, press ctrl + alt + f1

to see what's going on!

the issued seems to be ralated to the suspend and hibernate functions...

---

### Post by Hortichris on 2009-04-26
Also affects the HP DV9000 (dv9823em to be precise)

lot of prodding to get it to boot, to shut down hold the power button down for a while.  Curiously, plugging in part way through battery powered prodded booting, boot sequence proceeds normally.

No such problem with 8.04.

---

### Post by Hiimmat on 2009-04-30
I am having the exact same problem with my HP dv6000, the only difference is I have 4GB RAM.  I have tried to add an additional 512Mb to my swap partition, although I am not quite sure I did it successfully.  I have checked my power settings and restored them back to a default setting, and the problem still remains.  

Mathew

---

### Post by nitroguy on 2009-04-30
Same thing happened to me when I installed 8.10 on my 64bit dv9000.

This thread fixed it for me then, haven't tried it yet on 9.04

[http://ubuntuforums.org/showthread.php?t=1059545](http://ubuntuforums.org/showthread.php?t=1059545)

---

### Post by ryoga787 on 2009-05-01
I had the same problem in my HP Pavilion dv6000 with Ubuntu 8.10, with and without AC power. Now with 9.04 the problem only appears when I work with batteries, I solved it booting with the acpi=noirq option, but actually, I don't know how healthy is booting this way.

---

### Post by ebe0 on 2009-05-10
My laptop is HP dv6500 ([[COLOR="Red"]_dv6502au_[/COLOR]]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=in&docname=c01184507")) with ubuntu 9.04 amd64.
I too had a similar problem. In ubuntu 8.10 I had to hold down a key even when my laptop was connected to power to make it boot. In ubuntu 9.04 I had to hold down a key only when it was booting off battery power. 
There are a number of fixes to this problem:
1) Change the boot option in grub as suggested here
2) Downgrade your kernel (probably use an older version of ubuntu - i didn't have any problem with 8.04)
3) Update your bios
4) Recompile your DSDT file
There could be others, please share with the community if you find any.

Now it looks like an ACPI issue to me. And i'm not an expert in this.
 
Changing the boot option in grub will most likely disable the ACPI functionality which could be rather useful in a laptop.
Downgrading is not a realistic option for sooo many reasons.
You should upgrade the BIOS and see if it fixes this.
If not then we could recompile DSDT file.

Recompiling DSDT fixed it for me.

I followed the instructions in [[COLOR="Blue"]_How To Fix Your Buggy DSDT_[/COLOR]]("http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html") by snakedriver
and [[COLOR="Blue"]_HOWTO Fix A Buggy DSDT File_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt") by 67GTA
Please read the entire article (post(s)) before you do anything, also before making a new initrd image which is the last step you could make a copy of it, just in case.

Thanks you all.

---

### Post by avngrboy on 2009-05-17
Did anybody have a problem with the resolution when you installed ubuntu on your dv6000. I cant seem to fix it. Any help is appreciated.

---

### Post by sergiom99 on 2009-05-23
same thing here in Kubuntu JJ 32bits.
I found out that if I press any key during the booting process, Kubuntu loads fine.
Of course, it works perfect when plugged.
Resolution is fine though.

Edit> read somewhere this can be fixed by adding acpi_osi="Linux" to the grub line. anyone tried it?

---

### Post by sergiom99 on 2009-05-24
I tried adding *acpi_osi="Linux"* to the boot line in GRUB as suggested somewhere, but nothing. Upgraded to the latest BIOS version provided by HP, but nothing again.

---

### Post by sergiom99 on 2009-05-26
*bump*

---

### Post by sergiom99 on 2009-05-28
Here are my dmesg and syslog when I booted on battery to see if they help someone.
Thanks!

---

### Post by hughc1 on 2009-06-06
I have this problem.
Compaq Presarion F700  750US.
I tried the bios upgrade.  That didn't solve the problem.
Followed the instructions for the dsdt.dsl file.  I'm overwhelmed! Its 7373 lines of code!

---

### Post by ebe0 on 2009-06-13
To debug your DSDT file follow instructions in [[COLOR="Blue"]HOWTO Fix A Buggy DSDT File[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6527653&postcount=1") till you get to the place where you execute ```
iasl -tc /home/<yourusername>/dsdt.dsl
```. On executing the above command you'll get some errors and warnings. My output was like:
```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/urhome/dsdt.dsl   104:     Method (\_WAK, 1, NotSerialized)
Warning  1080 -                       Reserved method must return a value ^  (_WAK)

/home/urhome/dsdt.dsl  3540:                 Method (_Q16, 0, NotSerialized)
Warning  1087 -                                 Not all control paths return a value ^  (_Q16)

/home/urhome/dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1087 -                                 Not all control paths return a value ^  (_HOT)

/home/urhome/dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1080 -                                  Reserved method must return a value ^  (_HOT)

/home/urhome/dsdt.dsl  7716:                     Zero
Error    4095 -                            syntax error, unexpected PARSEOP_ZERO ^ 

/home/urhome/dsdt.dsl  7723:                 Method (_CRT, 0, Serialized)
Warning  1087 -                                 Not all control paths return a value ^  (_CRT)

/home/urhome/dsdt.dsl  7723:                 Method (_CRT, 0, Serialized)
Warning  1080 -                                  Reserved method must return a value ^  (_CRT)

/home/urhome/dsdt.dsl  7725:                     Zero
Error    4095 -                            syntax error, unexpected PARSEOP_ZERO ^ 

ASL Input:  /home/urhome/dsdt.dsl - 8137 lines, 278758 bytes, 4173 keywords
Compilation complete. 2 Errors, 6 Warnings, 0 Remarks, 1127 Optimizations
```

Then for every error/warning look for the error code and look it up in [[COLOR="Blue"]How To Fix Your Buggy DSDT[/COLOR]]("http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html"). Chances are you'll find all the fixes there, else you can always google for them.

For example:
for
 ```
/home/urhome/dsdt.dsl   104:     Method (\_WAK, 1, NotSerialized)
Warning  1080 -                       Reserved method must return a value [CODE]
```^  (_WAK)[/CODE]
I added **Return(Package(0x02){0x00, 0x00})** to the end of the function **Method (\_WAK, 1, NotSerialized)** (just befor the final close of the function)

and for 
```
/home/urhome/dsdt.dsl  7716:                     Zero
Error    4095 -                            syntax error, unexpected PARSEOP_ZERO ^ 
```
In the function **Method (_HOT, 0, Serialized)** I commented out Zero just bellow the function like so:
```
Method (_HOT, 0, Serialized)
                {
                    //Zero
```

after fixing the other errors/warnings i got the following o/p 
```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/urhome/dsdt.dsl  7716:                 Method (_HOT, 0, Serialized)
Warning  1087 -                                 Not all control paths return a value ^  (_HOT)

/home/urhome/dsdt.dsl  7716:                 Method (_HOT, 0, Serialized)
Warning  1080 -                                  Reserved method must return a value ^  (_HOT)

/home/urhome/dsdt.dsl  7725:                 Method (_CRT, 0, Serialized)
Warning  1087 -                                 Not all control paths return a value ^  (_CRT)

/home/urhome/dsdt.dsl  7725:                 Method (_CRT, 0, Serialized)
Warning  1080 -                                  Reserved method must return a value ^  (_CRT)

ASL Input:  /home/urhome/dsdt.dsl - 8139 lines, 278832 bytes, 4175 keywords
AML Output: /home/urhome/dsdt.aml - 31944 bytes, 821 named objects, 3354 executable opcodes

Compilation complete. 0 Errors, 4 Warnings, 0 Remarks, 1130 Optimizations

```

I was not able to eliminate all the warnings, however i got all errors and it worked.

Please let me know if this helps.

Regards
Ebe

---

### Post by sergiom99 on 2009-06-18
Today I upgraded to
```
$ uname -a
Linux kubuntu 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux
```

But it's still not solved.

---

### Post by sergiom99 on 2009-06-25
I got it fixed by fixing my DSDT with this awesome howto [1] and thanks to 67GTA's kind help.
Take a look and help yourselves, its not difficult at all!
Good luck! 
-Sergio

[1] [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by mlitty on 2009-07-20
> It's not difficult at all
Really?  This reminds me of my first Hebrew class.  Except that there wasn't the threat of bricking my laptop at the end of the first homework assignment.  

Having to plug in my laptop every time I use it sucks, but the thought of bricking it over a type is more than I can take at this point.

I know it's not Linux's fault, but I thought things had improved beyond this point.  Life shouldn't be this difficult.

---

### Post by cespinal on 2009-08-13
****bump***** 
this is still being a problem for a lot of folks here

---

### Post by sergiom99 on 2009-08-13
> **sergiom99 said:**
> I got it fixed by fixing my DSDT with this awesome howto [1] and thanks to 67GTA's kind help.
Take a look and help yourselves, its not difficult at all!
Good luck! 
-Sergio

[1] [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

Check this thread and give it a try. Its easy.

And submit a bug in Launchpad, so as to make kernel devs fix this issue.
> **67GTA said:**
> I have filed a bug report on launchpad for my machines that are affected. The kernel devs are removing the dsdt patch in order to get more kernel bug reports. The idea is to try and fix the problems we are dealing with in this thread. With 9.10 and on, you will have to compile a custom kernel to use a custom dsdt. I will see if my bugs can be fixed by 9.10. If you want to try the same, create an account here: [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) Once that is done, open a terminal and run ```
ubuntu-bug -p linux
  
``` This will gather all of the needed reports for you and post them after you finish the report. All of the bugs fixed by editing the dsdt are considered kernel bugs. The "linux" package is the kernel. I will still fix dsdt's if you ask or help you figure out what to put in the bug report. (see: [http://ubuntuforums.org/showthread.php?t=1036051&page=25](http://ubuntuforums.org/showthread.php?t=1036051&page=25))

---

### Post by HolyShnikes on 2009-09-16
*Bump*

I have the same problem.  Is this also related to when I go into sleep mode the screen wont come back on?  

Anyone tested it to see if any of the above options worked?  I would have to try something for a long time only to find out it doesnt work.  As of yet, I don't think anyone responded that it has been fixed.  

I was about to make a new thread for this, but I thought I would just add on this one.  Any luck?

---

### Post by sergiom99 on 2009-09-16
It gets fixed if you make a DSDT file for your specific hardware.

You're also welcomed to file bug reports at launchpad.

---

### Post by 3nd3r on 2009-10-20
I have a F759WM Compaq laptop with the same issue.
I find that using acpi=noirq in my grub config on the kernel line fixes all of my issues.

---

