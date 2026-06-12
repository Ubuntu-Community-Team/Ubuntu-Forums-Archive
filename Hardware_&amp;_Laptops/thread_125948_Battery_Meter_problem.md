---
title: "Battery Meter problem"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by rickbath on 2006-02-05
Hi, 

I am using Acer TM 4102WLMi . I have problem getting my power management 
to work. My batt meter seems to have a problem displaying the correct batt meter...


Would appreciate if someone could assist me out.

---

### Post by rickbath on 2006-02-06
could someone help me out here.......

---

### Post by lolcese on 2006-02-06
Have you put acpi=on in the menu.lst? The battery meter shows wrong measurements or no measurements at all?

---

### Post by Greg2 on 2006-02-06
I have to use acpi=strict for my HP battery status. You could try that if acpi=on doesn’t work properly, and I’ve also read that some have used acpi=force.

If you do a search for 'kernel boot parameters' you will find many more and what they do... because it may take a combination of two or more for ‘your’ laptop.

---

### Post by skirkpatrick on 2006-02-07
No real problems with my HP laptop but here's what I had to go through to get it and networking working on my son's Acer Aspire 3003LXCI:
[http://www.ubuntuforums.org/showthread.php?t=60484](http://www.ubuntuforums.org/showthread.php?t=60484)

---

### Post by rickbath on 2006-02-07
hi,

i have tried all of the above but, my gnome-power-manager still shows 0%
do i need to run anything after i do the changes ?

here is the config


title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro vga=771 noapic nolapic quiet splash acpi=strict
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro vga=771 noapic nolapic single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

---

### Post by lolcese on 2006-02-07
Why are you including noapic nolapic as parameters?

---

### Post by rickbath on 2006-02-07
it wont boot without it

---

### Post by lolcese on 2006-02-07
I'm not 100% sure, but I think that [FONT=Courier New]noapic[/FONT] means "no acpi", so maybe this is the problem. In which stage the boot halts without the [FONT=Courier New]noapic nolapic?[/FONT]

---

### Post by Greg2 on 2006-02-07
[QUOTE=rickbath]
here is the config


title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro vga=771 noapic nolapic quiet splash acpi=strict
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot[/QUOTE]
I ‘believe’ you should list ‘quiet splash’ last? (not really sure about it)

kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro vga=771 noapic nolapic acpi=strict quiet splash 

You might also try adding acpi=noirq and irqpoll if you still have problems? Like this:

kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro vga=771 noapic nolapic acpi=strict acpi=noirq irqpoll quiet splash

---

### Post by rickbath on 2006-02-07
[QUOTE=Greg2]I &#8216;believe&#8217; you should list &#8216;quiet splash&#8217; last? (not really sure about it)

kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro vga=771 noapic nolapic acpi=strict quiet splash 

You might also try adding acpi=noirq and irqpoll if you still have problems? Like this:

kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro vga=771 noapic nolapic acpi=strict acpi=noirq irqpoll quiet splash[/QUOTE]


tried but, dont work

---

### Post by Greg2 on 2006-02-07
[QUOTE=lolcese]I'm not 100% sure, but I think that [FONT=Courier New]noapic[/FONT] means "no acpi", so maybe this is the problem. In which stage the boot halts without the [FONT=Courier New]noapic nolapic?[/FONT][/QUOTE]
I&#8217;m not sure, but I &#8216;think&#8217; that would be acpi=off

A quick search found this:
[http://www.cs.helsinki.fi/linux/linux-kernel/2002-13/0204.html](http://www.cs.helsinki.fi/linux/linux-kernel/2002-13/0204.html)

So you could try this:

title Ubuntu, kernel 2.6.12-9-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro vga=771 acpi=strict acpi=noirq pci=biosirq pci=nosort irqpoll routeirq quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

---

### Post by rickbath on 2006-02-07
same prob....:( :(

---

### Post by rickbath on 2006-02-08
any suggestions ....

---

### Post by rickbath on 2006-02-08
not sure if this helps out....

rick@ubuntu:~$ cat /proc/acpi/battery/BAT1/state
present:                 yes
ERROR: Unable to read battery status
rick@ubuntu:~$

---

### Post by rickbath on 2006-02-09
still awaiting help from a kind soul.....

---

### Post by nwcowboysfan on 2006-02-09
probably a DSDT problem, the below linked fixed a few of the problems but battery monitor is still not working exactly right.

[https://wiki.ubuntu.com/ACPIBattery?highlight=%28battery%29](https://wiki.ubuntu.com/ACPIBattery?highlight=%28battery%29)

good luck

---

### Post by rickbath on 2006-02-11
i am having the following problem....

there is only one dsdt downloadable for my version. it says 
1.25GB DDR. but, mine came originally with 512MB and i upgraded
to 1Gb. dont think it matters though...

root@ubuntu:/home/rick/downloads/acpi# ./iasl -tc dsdt.asl

Intel ACPI Component Architecture
ASL Optimizing Compiler / AML Disassembler version 20050624 [Feb 11 2006]
Copyright (C) 2000 - 2005 Intel Corporation
Supports ACPI Specification Revision 3.0

dsdt.asl   364:                     0x0100, 0x00)
Error    1094 -                                 ^ Missing ResourceSource string (required)

dsdt.asl   370:                     0x00020000, 0x00)
Error    1094 -                                     ^ Missing ResourceSource string (required)

dsdt.asl   376:                     0x00004000, 0x00)
Error    1094 -                                     ^ Missing ResourceSource string (required)

dsdt.asl   382:                     0x00004000, 0x00)
Error    1094 -                                     ^ Missing ResourceSource string (required)

dsdt.asl   388:                     0x00004000, 0x00)
Error    1094 -                                     ^ Missing ResourceSource string (required)

dsdt.asl   394:                     0x00004000, 0x00)
Error    1094 -                                     ^ Missing ResourceSource string (required)

dsdt.asl   400:                     0x00004000, 0x00)
Error    1094 -                                     ^ Missing ResourceSource string (required)

dsdt.asl   406:                     0x00004000, 0x00)
Error    1094 -                                     ^ Missing ResourceSource string (required)

dsdt.asl   412:                     0x00004000, 0x00)
Error    1094 -                                     ^ Missing ResourceSource string (required)

dsdt.asl   418:                     0x00004000, 0x00)
Error    1094 -                                     ^ Missing ResourceSource string (required)

dsdt.asl   424:                     0x00000000, 0x00)
Error    1094 -                                     ^ Missing ResourceSource string (required)

dsdt.asl   431:                     0x0CF8, 0x00)
Error    1094 -                                 ^ Missing ResourceSource string (required)

dsdt.asl   437:                     0xF300, 0x00)
Error    1094 -                                 ^ Missing ResourceSource string (required)

ASL Input:  dsdt.asl - 3050 lines, 107905 bytes, 1404 keywords
Compilation complete. 13 Errors, 0 Warnings, 0 Remarks, 467 Optimizations

---

### Post by nwcowboysfan on 2006-02-14
i didn't experience these problems, but below is a link with a HUGE thread of people having various errors. may be worth while to scan through the thread.

good luck

[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

---

### Post by Crayoneater on 2006-02-15
[QUOTE=rickbath]not sure if this helps out....

rick@ubuntu:~$ cat /proc/acpi/battery/BAT1/state
present:                 yes
ERROR: Unable to read battery status
rick@ubuntu:~$[/QUOTE]

i had this same problem, and i fixed it by using the kernel boot option: 

acpi_os_name=Microsoft Windows 2000

you have to fiddle around with different windows version such as:
Microsoft Windows 2000
Microsoft Windows 2000.1
Microsoft Windows XP

that fixed my problem...i tried Microsoft Windows XP and the battery sort of worked, but when i used 2000 it works perfectly.

EDIT: I have an Acer Aspire 5002WLMi by the way, and i spent a long time messing around with those dsdt files, and finally came across this solution that didn't require any messing with files or anything....just a simple boot option...make sure to try all of the os names, because some might work better than others....

---

### Post by davidU on 2006-04-02
[QUOTE=Crayoneater]i had this same problem, and i fixed it by using the kernel boot option: 

acpi_os_name=Microsoft Windows 2000

you have to fiddle around with different windows version such as:
Microsoft Windows 2000
Microsoft Windows 2000.1
Microsoft Windows XP

that fixed my problem...i tried Microsoft Windows XP and the battery sort of worked, but when i used 2000 it works perfectly.

EDIT: I have an Acer Aspire 5002WLMi by the way, and i spent a long time messing around with those dsdt files, and finally came across this solution that didn't require any messing with files or anything....just a simple boot option...make sure to try all of the os names, because some might work better than others....[/QUOTE]

Hi,
I read your post with great interest as I have a battery status problem on my Toshiba L10 laptop.
I'd like to fix it but I'm afraid most of what you wrote went completely over my head.
First question: How do I get to the kernel boot options ?

---

