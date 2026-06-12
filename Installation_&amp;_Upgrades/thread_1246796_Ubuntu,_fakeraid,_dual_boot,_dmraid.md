---
title: "Ubuntu, fakeraid, dual boot, dmraid"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by ginx on 2009-08-22
Hello all,

I'm a total noob to Linux, and have chosen to use Ubuntu as my distro of choice.
I was very eager to start using Linux. But, as you may have already figures this out I have had some problems with installing Ubuntu on my system.

I have three HDDs. Two of them (500GB WD) in a software raid 0 (via nvidia controller). The third one is a separate 160GB WD HDD.
I have XP (x64) installed on the raid HDDs, an older XP (x64) installed (not in use) on the separate HDD. The third (and separate HDD) has two NTFS partitions (one is used by the XP installation), one EX4 partition and one swap partition. I was trying to install Ubuntu on the third HDD.
As you may have already guessed, I did not seceded installing successfully Ubunto onto my system. Ubuntu and GRUB have a problem detecting, installing and booting alongside software raid. Neither the Linux nor the XP install will boot.
During the installation, the installer did not recognize the XP installed on the raid drive (not so surprisingly), it didn't also recognize (suprisingly) the XP installed on the separate HDD.
Making the third HDD the primary boot HDD and installing (again) Ubuntu did not help, neither Unbuntu nor the older XP install are booted.
I've been at it for about a week, looking for away to solve the problem. I have found all sorts of guides: [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"), "[Getting GRUB to recognize a windows installation on a RAID0 array]("http://ubuntuforums.org/archive/index.php/t-1092764.html")" and many more. I couldn't solve the problem using the. For instance, I get stuck in the middle of the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto") guide, and do not know how to continue.

Another matter I have found relevant. Apparently there is a known open issue (bug?) regarding dmraid being integrated into Ubuntu installer (just as been done with Fedora apparently). Was this issue solved in the upcoming Karmic Koala release?


As I have said, I am new to Linux, and thus far did not loose the desire to use Linux. Please help me to solve the issue and start using Ubuntu. I will appreciate any help.

Thank you,
ginx.

---

### Post by ginx on 2009-09-04
[FONT=Arial]No one is able to give me some sort of an answer? I still want to install ubuntu, but thinking about installing Fedora (that suppose to have built-in support for dmraid). Or should I wait for the next release of ubuntu?




 Again, thank you in advance.[/FONT]

---

### Post by Kristofer Van Orton on 2009-09-04
I'm not sure i completely understand, how many operating systems in total are you trying to dual boot?
Have you already installed ubuntu but can't access it?
answer and i may be able to help
-KVO

btw Ubuntu is good for noob users
as compared to fedora

btw again :P karmic koala is in testing
if you wanted to try that it would be better to only install for testing purposes until the full version comes out

---

### Post by ronparent on 2009-09-04
What step in the FakeraidHowTo are you getting stuck on? 

I agree, installing ubuntu to a fakeraid is not as straight forward as it should be. Another hitch is a rare bug that prevents dmraid from activating the raid array on boot. I haven't heard much about that lately however.

---

### Post by ginx on 2009-09-05
> **Kristofer Van Orton said:**
> I'm not sure i completely understand, how many operating systems in total are you trying to dual boot?
Have you already installed ubuntu but can't access it?

I have Win XP pro x64 on the raid array, and Ubuntu on the additional hdd.

> **ronparent said:**
> What step in the FakeraidHowTo are you getting stuck on? 

At the "Ubuntu 9.04" section I get stuck on step i.



Another interesting matter, I have installed win xp all over (could not repair the MBR via windows repair). Windows does recognize that Ubuntu is installed (I get a choice menu - to choose what operating system I want to load), but when I choose Ubuntu it searches for "ntoskrnl.exe". What does that mean? The boot loader "thinks" that the additional OS is windows?

Thanks for the help.

---

### Post by ronparent on 2009-09-05
Phew. Sorry I asked. This HowTo seems to be drastically expanded since I last used it 6 months ago.

I get the uneasy feeling that steps i and j are in the wrong order. Grub should install to /boot/grub. If that were the case the file location should exist after grub installation unlees grub installed elsewhere? I am in win 7 now with no access to raid on this system. I'll have to check when I get my raid0 system back online. Otherwise the steps before and after this seem to track properly. I'll have to get back on this one.

---

### Post by ginx on 2009-09-05
I appreciate the help ronperant. Thank you.__

---

### Post by ronparent on 2009-09-05
I must just be learning to read. Did you say that ubuntu is on the additional hard disk? If that is the case is it raid0 also? If not, the problem could be very simply solved,

If ubuntu is not on a raid, you don't need the fakeraidHowTo! The simplest thing to do is to change the boot order in bios so that the additional disk is first in boot order. You can then perform a normal install with the live cd and grub will be automatically written to the mbr of that drive and find your new install. You may have to fix grub to load windows. But in any case you will be able to get to it by restoring the boot order. You may need some instruction to automatically mount a window partition if you need access to data on the windows drive. But that is another issue.

I, incidently, have a machine in which I have installed ubuntu on a separate drive from my windows xp install on a raid0. Until I figured out the grub thing I would dual boot by changing boot order in bios.

---

### Post by addohm on 2009-09-17
I've successfully done a Raid0 configuration, dual booting with Windows 7, using dmraid, with Gentoo.  Gentoo allows you to pass an argument with the genkernel command, that compiles dmraid in to the kernel, making the raid started\seen at boot.  With ubuntu, I've yet to find a proper work around to getting it to work; I believe Ubuntu needs to go the same route.  "Fakeraids" are getting more and more common, and the difficulty of installing\configuring linux boot loaders to use them properly, only makes people turn their backs.  I've got two blank, unused, partitions on my PC, waiting for a better ubuntu.

---

