---
title: "ACPI &quot;Unable to read battery status&quot;"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by niffshack on 2005-07-14
I recently got a laptop (acer aspire 3000), and I heard ubuntu was good, so I decided to try it out, and so far its been great.

Only one problem: ACPI isn't able to read the battery status. It can tell whether it's plugged in or not, but I don't get any percentages, time remaining, etc.

Looking into /proc/acpi/battery/BAT1/state, I get this:
```
present:                 yes
ERROR: Unable to read battery status
```

I'm not sure what to do... I have no experience with ACPI... The battery worked fine under winxp, but I'd much rather use ubuntu and not worry about running out of battery. Is this a common problem? Is it kernel-related? Any Ideas?

---

### Post by briguy on 2005-07-15
My battery monitoring doesn't work out of the box either, and it's due to poor DSDT coding by the manufacturer.  You should be able to fix it using the instructions [here](http://gaugusch.at/kernel.shtml) .  The ubuntu kernel is already patched to accept the initrd method.  You can find a patched version of your DSDT [here](http://acpi.sourceforge.net/dsdt/index.php) .  This fixed the problem for me.

---

### Post by niffshack on 2005-07-15
Alright, so I found the dsdt, but I'm not quite sure what to do with the initrd...

Should I append the "magic signature" and dsdt file to the already existing initrd? Should I replace the existing initrd (wouldn't this damage the startup sequence)?

That doesn't really seem right though...

Also, the file I found is a .asl file, it appears to be a "dissassembled" .aml file (Human-readable, looks like source code), should this be compiled?

(EDIT: I didn't read far enough, it does have to be "assembled"... Though I'm not sure where to get the assembler "iasl")

---

### Post by niffshack on 2005-07-15
Well, I found iasl... But now I'm getting some errors trying to compile...
```
Intel ACPI Component Architecture
ASL Optimizing Compiler / AML Disassembler version 20050624 [Jul 15 2005]
Copyright (C) 2000 - 2005 Intel Corporation
Supports ACPI Specification Revision 3.0

dsdt.dsl  2506:                             If (LNot (LEqual (\_PR.CPU0._PPC, Zero)))
Error    1022 -                                      Object does not exist ^  (\_PR.CPU0._PPC)

dsdt.dsl  2508:                                 Store (Zero, \_PR.CPU0._PPC)
Error    1022 -                                     Object does not exist ^  (\_PR.CPU0._PPC)

dsdt.dsl  2516:                             If (LLess (\_PR.CPU0._PPC, Local1))
Error    1022 -                               Object does not exist ^  (\_PR.CPU0._PPC)

dsdt.dsl  2518:                                 Store (Local1, \_PR.CPU0._PPC)
Error    1022 -                                       Object does not exist ^  (\_PR.CPU0._PPC)

dsdt.dsl  2528:                         If (LNot (LEqual (\_PR.CPU0._PPC, Zero)))
Error    1022 -                                  Object does not exist ^  (\_PR.CPU0._PPC)

dsdt.dsl  2530:                             Store (Zero, \_PR.CPU0._PPC)
Error    1022 -                                 Object does not exist ^  (\_PR.CPU0._PPC)

dsdt.dsl  3387:     Method (_WAK, 1, NotSerialized)
Warning  2026 -                ^ Reserved method must return a value (_WAK)

ASL Input:  dsdt.dsl - 3467 lines, 119922 bytes, 1560 keywords
Compilation complete. 6 Errors, 1 Warnings, 0 Remarks, 3 Optimizations
```

This isn't looking good...

---

### Post by edheil on 2005-07-15
You need to install the package "flex-old" instead of "flex" to make iasl compile.

I guessed this by doing apt-cache show flex, and noting that this version of flex has incompatible changes from older versions.

---

### Post by ecliptik on 2005-07-15
I don't have an Acer, but with me Dell that wasn't reporting battery status correctly I found the solution lay in updating the BIOS. It was about 20 revs out of date, and once I did the update it worked like a charm, fixed a whole lot of other issues as well.

---

### Post by edheil on 2005-07-15
I just checked and the bios on my ACER aspire 3002LCI is up to date.

I got the battery thing working!

Needed to do the following tricks --

install flex-old instead of flex to compile iasl from intel

I used this dstd:

[http://acpi.sourceforge.net/dsdt/view.php?id=405](http://acpi.sourceforge.net/dsdt/view.php?id=405)

I patched that dstd with the patch from this message:

[https://sourceforge.net/mailarchive/message.php?msg_id=11919655](https://sourceforge.net/mailarchive/message.php?msg_id=11919655)

which allowed the dstd to compile.  (THe last chunk of the patch was rejected, but it worked anyway).

BTW, I totally trashed my install by accidentally using > instead of >> and wiping out my initrd img the first time I tried it!  BACK THAT THING UP before you mess with it and have a recovery CD handy just in case!!

---

### Post by niffshack on 2005-07-15
Well...
It works now! Thanks! It was that patch that fixed it... And as for using the wrong I/O redirector... Ouch...

Once again, thanks!

---

### Post by GerritKok on 2005-07-20
[QUOTE=edheil]

I used this dstd:

[http://acpi.sourceforge.net/dsdt/view.php?id=405](http://acpi.sourceforge.net/dsdt/view.php?id=405)

I patched that dstd with the patch from this message:

[https://sourceforge.net/mailarchive/message.php?msg_id=11919655](https://sourceforge.net/mailarchive/message.php?msg_id=11919655)

which allowed the dstd to compile.  (THe last chunk of the patch was rejected, but it worked anyway).[/QUOTE]

Did you replace the Z007 for 'Ones'? If yes, how do you do that?

I have the same problem with Aspire 3503. dmesg gives loads of:
[I]ACPI-0352: *** Error: Looking up [Z004] in namespace, AE_NOT_FOUND search_node db9a1280 start_node db9a1280 return_node 00000000    
 ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node db9a1180), AE_NOT_FOUND [/I] 

I wonder if i could do the same with Z004?

Gerrit

---

### Post by Confuse on 2005-07-20
I have the same exact laptop and problem but fixed it in a similar way, congrats. By the way, how do you like your acer laptop? What do you think of the screen quality? Bummer about the battery. hehe

Damian

---

### Post by GerritKok on 2005-07-21
I have the Aspire 3503 notebook now for a week and i'm happy with it and the screen is beautiful (I thought i had a good quality CRT connected to my PC, but th poor thing now looks terribly fuzzy and outdated). The notebook gets a bit warm though (61C) but i understood this is something not to worry too much about. First of all i  want to fix this battery-monitoring problem. I understand you fixed the problem on your machine. 

.......but i'm still in the dark. 

And i'm not at all experienced in kernel patching and stuff and just a little in syntax so what i need is somebody who takes me by the hand and guides me through this challenge. Replacing Z004 by 1111 seems easy but to be honest, i haven't got a clue how to do this. So i would be very happy with all guidance of you and all the other specialists out there.

Gerrit

---

### Post by smyfek on 2005-09-29
I have the same problem with my laptop Acer TravelMate 2305LCI. I can't see my battery status. I heve tried to fix it by reading "wiki battery how to" but I couldn't find DSDT for my model TravelMate 2305LCI and I used 2312LCI file but still doesn't work :(

Is there anyone who has the same Laptop model and fix this problem ?

Many thanks,
Smyfek

---

### Post by Toky on 2005-10-12
I'm on the same boat, i have a Acer Aspire 3002 and my wi-fi nor my ACPI are working.....

I d/l the dst file (patch) and ran the command on the website 
"toky@laptop:~$ patch -p1 /home/toky/acpi-dsdt-initrd-v0.7d-2.6.12.patch"  <-- my command
but it just hangs.... i left it there for about 3hrs (since the laptop is only a sempron) but it stayed hanged, so i killed it.  I kept using the laptop for 6 more hrs, then i shutit down and tookit home, but when i turned it on....i had NO DISPLAY whatsoever....

nothing, nada, kaput..... so i was wondering if that attemtp at the patch could've killed my display?

I don't see anything on the display, not even the acer logo when the laptop is POSTing, I can connect a monitor to the laptop and use it (doing it now) but cant use it without the monitor.

any ideas???

I'm using Breezy...

---

### Post by skirkpatrick on 2005-10-12
I've got both wifi and battery working on my Acer 3002 with Breezy.  Wifi signal strength doesn't work but that's supposed to be a problem with ndiswrapper.  Check out my thread at [http://www.ubuntuforums.org/showthread.php?t=60484](http://www.ubuntuforums.org/showthread.php?t=60484).

---

### Post by Toky on 2005-10-12
Thanks for the reply, i've seen your post (got it as a bookmark)
but what i need to know is, if the hanged attempt to patch the dst file could've disabled my display????

I won't work on the wireless or the acpi until i get the display issue worked out, since i might have to send the laptop back to acer if the display is broken i dont see much sense in getting it to work so i hava to re-do it when i get the replacement laptop.

---

### Post by skirkpatrick on 2005-10-13
Now I think I understand.  If I follow you correctly, you inserted the DSTD into the kernel as I don't think letting the kernel load it works very well under Hoary.  If that is the case, you've probably trashed your kernel.  Since you can't get into it to fix it anyway, I'd recommend reinstalling Ubuntu over the top of it.  If you are dual-booting with Windows, install Ext2IFS from [http://www.fs-driver.org/](http://www.fs-driver.org/) which will allow your Windows to read/write your Linux partition.  That way you can save off any critical files you had before you reinstall.

---

### Post by Toky on 2005-10-13
well, letme get the new breezy, and i'll re-install it.

But i dont think its the kernel the issue here.... since i don't see a display at all, when i turn the laptop on nothing happens in the display....  i'll check the display cables after installing breezy (if that doesn't fix it)

Thanks for ur reply

---

### Post by skirkpatrick on 2005-10-13
Changing the kernel shouldn't have done any real damage to your display and it wouldn't have actually changed your BIOS.  Can you get into your BIOS setup?  Can you connect it to a monitor and see if you get anything?  This doesn't sound too good.

---

### Post by Toky on 2005-10-15
Yes I can connect a monitor to it and use it, but i can't use the laptop's display, i'll reconect it to a monitor and see if i can get to BIOS (although i doubt it)

---

### Post by skirkpatrick on 2005-10-15
Toky, maybe something is wrong with the backlight?

---

### Post by nateU on 2005-10-27
Hi, I have been having the same problems with the ACPI and such, I have Acer 3002.  I built the iasl compiler, and when I make the new hex file and try to patch it says to me
```
 ****nothing but garbage in patch file.
```

Does anyone know what is causing this? I am running breezy, and I am very new to linux.

I am using the patch command I found in the HOWTO , it goes like this
```
patch -p1 -i /path/to/dsdt.hex
```

---

### Post by skirkpatrick on 2005-10-27
As far as I know, there's no patch to apply.  This post in particular, [http://www.ubuntuforums.org/showpost.php?p=387628&postcount=18](http://www.ubuntuforums.org/showpost.php?p=387628&postcount=18), should get you a working DSDT.

---

### Post by nateU on 2005-10-27
[QUOTE=skirkpatrick]As far as I know, there's no patch to apply.  This post in particular, [http://www.ubuntuforums.org/showpost.php?p=387628&postcount=18](http://www.ubuntuforums.org/showpost.php?p=387628&postcount=18), should get you a working DSDT.[/QUOTE]
Thanks, I will definitely give that a try.  Maybe the tutorials I have found on google are for older kernels.

---

### Post by skirkpatrick on 2005-10-27
I believe you are correct, the older kernels (not sure how old but older than Hoary) required patches to work correctly.

---

### Post by nateU on 2005-10-27
Well I got it working, it took a few attempts but I finally got it to compile without any errors and I am now able to see my battery status.  Thank you so much for helping.  I must say though, it is kind of depressing to see that at 98% I only have about an hour left.  They sure put a cheapo battery in this thing... 
One more thing, did the fixed DSDT allow you to make use of the various function buttons, like the wireless and bluetooth?  I would like to map them to some function if at all possible.

Step 2: Wireless with NDISwrapper, hopefully that won't give me as much grief.

---

### Post by skirkpatrick on 2005-10-27
I'm glad to hear it!

Follow the rest of that thread to get wireless working.  Also, check out [http://ubuntuforums.org/showthread.php?t=75820](http://ubuntuforums.org/showthread.php?t=75820) where the Acer battery/wifi thread has been continued for Breezy.

If you follow those two threads, one of the things you will see that you need to build and install is acerhk.  You'll need it for wifi to work (it turns on the radio) and it will give you the ability to use your non-standard buttons.  Check out [http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/) about setting up your buttons (I haven't done anything with them).

---

### Post by stengah on 2006-04-13
I must correct my previous advice and learn to walk though the threads prior to posting other 'possible' soliutions. I can only recommend skirkpatric's guide to the battery indicator problem above.

I'll be looking into the other threaded hints (wifi/radio) tomorrow- thanks again!

---

### Post by stengah on 2006-04-14
[QUOTE=skirkpatrick]As far as I know, there's no patch to apply.  This post in particular, [http://www.ubuntuforums.org/showpost.php?p=387628&postcount=18](http://www.ubuntuforums.org/showpost.php?p=387628&postcount=18), should get you a working DSDT.[/QUOTE]

Skirkpatrick: You've saved my day - this excellent post with the step-by-step tutorial of yours solved the lacking battery status indicator problem on my Acer Aspire 3005 - all changes came to effect after a reboot. :-D

---

