---
title: "Gigabyte GA-965P-DS3 segmentation fault when booting any ubuntu version?"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by MiniMower on 2007-10-21
Hello

I've just upgraded my motherboard, chip and harddrive and am trying to install ubuntu again.

My spec

Gigabyte GA-965P-DS3 motherboard
Intel 2.8 Ghz Core Duo chip
2 gig memory
Sata harddrive plugged into Yellow Sata port 0
Sata DVD driver plugged into Yellow Sata port 0
Nvidia graphics plugged into pci express slot

Getting different results when trying different options on different cds

no live versions work and all stall with just a flashing cursor in the top right before even the loading bit comes up.

if i just try to install with the other cd i can sometimes get to the installer. but it keep saying segmentation fault over and over as it is trying

i can boot damn small linux if i choose the minimal hardware detection option then it does come up to desktop.

i've been people having a lot of problems with this motherboard? i've tried a few different settings on the motherboard regarding sata and ide detection etc which gives different results.

Anyone got this motherboard and got it to install? if so please let me know bios settings you have? i've updated the bios to the new version but can't see any differences.

any suggestions that may help me?

---

### Post by MiniMower on 2007-10-21
at first i had an sata harddrive and a ide cd writer and i thought this might be the problem.

so i've brought a sata cd drive but hasn't helped at all

but i've noticed on the board if i try the purple raid ports it's even worse

and i use an ide harddrive and ide cd drive i still get segmentation faults during boot

---

### Post by MiniMower on 2007-10-21
ok booting from the gutsy live cd i just just the cursor flashing in top left even if i choose normal or failsafe boot

with alternative cd i get a little further if i choose install text version. i get segmentation faults regarding unable to detect system memory? rebooted twice and got the same message both times?

---

### Post by MiniMower on 2007-10-21
ok progressing with the alterative install

tried acpi=off  but didn't help

i'm getting segmentation faults with debconf cannot initiziate

can some please help?

when trying damnsmalllinux i can get dmesg up

errors are 

ACPI:IRQ9 Error: Method Execution Failed

and

Failed initization of WD-7000 SCSI card

and

apm: overwritten by ACPI

---

### Post by MiniMower on 2007-10-21
bump

---

### Post by MiniMower on 2007-10-21
bump

---

### Post by MiniMower on 2007-10-22
can someone please help me

---

### Post by MiniMower on 2007-10-22
bump

tried the amd64 version but get a kernel parnic and don't get as far

if i boot the new gutsy live cd then it halts at the loading kernal

guessing it's my motherboard with the 965p chipset causing all the problems and wondered if anyone has this motherboard working???????

---

### Post by Axdrenalin on 2007-10-22
I was browsing the forums and noticed your post. I'm new to Linux other than just tinkering over the past couple years, but wanted to let you know that I've got the same motherboard (GA-965P-DS3 Rev 3.3) and have had no problems at all with loading Ubuntu. I've got the 7.10 64 bit version loaded up, and while I haven't had time to tinker much with it, everything seems to work without issue.

I am using SATA 0 for the HD, and IDE1 for the DVDRW drive.

What revision is your MB, as well as your other specs?

Don't know if there is much I can give you other than the specs and knowledge that things are working well with my boxen. Have you run a good hardware test on it, like maybe Prime95 to stress test your hardware?

Just for reference, these are my specs:

Gigabyte GA965P-DS3 Rev 3.3
E4300 C2D 
2 Gigs Corsair PC2-6400 DDR2
Seagate 80 gig SATA HD
Lite-On DVD-RW
NVidia 7600GS / 256

TTYL,

Ax

---

### Post by MiniMower on 2007-10-31
hello

thank you for your reply

ok i will try the 64bit version then?

one of my problems was 2 different memory speeds on the motherboard.

i have my harddrive is sata0 and dvdrw in sata 1. buti have a ide dvd writer so will try that in ide1 in a second

i will post my finding in a moment.

what are your bios settings for AHCI? or ACPI? do you have them set to ide?

many thanks

---

### Post by MiniMower on 2007-10-31
thank you for your help

i've finally got the installer up ok

i have sata0 harddrive and ide cd rom

my system won't boot if i have cdrom is sata1?? anyway i am making progress now

but note i am not using the 64bit version? just the normal but installer if doing it's stuff now

many thanks

---

### Post by ZanexGt on 2007-11-09
I have the same motherboard and have had no problems with the Gutsy live CD or the Feisty CD. 

I run a 500GB wd SATA II hd and an IDE dvd/cd burner.

---

