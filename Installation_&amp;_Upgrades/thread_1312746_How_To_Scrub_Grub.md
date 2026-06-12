---
title: "How To Scrub Grub"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Yogi2 on 2009-11-03
My computer system contains two hard drives.  Initially drive0 had Vista installed and drive1 had Fedora installed.  The method of switching from one OS to the other was to enter BIOS, and to manually select from which hard drive to run.  Not elegant, but it kept Linux and Windows well separated and trouble free.

Recently I installed Ubuntu 9.10 onto drive1 overwriting the Fedora installation.  However, now the Grub loader comes up each time I turn on the power to my computer.  Both Windows and Ubuntu seem to be working fine, but I prefer not to use Grub to select an OS.  I would like to go back to the original configuration wherein I could go into BIOS and manually select which drive (OS) to boot up.  Is it possible to do this?

If I can't uninstall Grub, is it possible to change the default OS on it's menu to something other (Vista in my case) than Ubuntu?

---

### Post by sliketymo on 2009-11-03
Edit  /etc/default/grub.

---

### Post by Yogi2 on 2009-11-03
Is editing the file the only solution?  
Can Grub be uninstalled?

---

### Post by presence1960 on 2009-11-03
It is your machine, you can do whatever you wish. Out of curiosity why would you want to have to go into BIOS to select an OS when GRUB is doing it for you?

Your OSs are still separate and distinct, GRUB has not changed that. All GRUB does is point to the files necessary to boot the OS you choose. Which is in effect the same thing you do when going into BIOS- you are choosing which MBR to look to for bootloaders when you choose the hard disk in BIOS. Why would you want that extra step involved?

---

### Post by presence1960 on 2009-11-03
> **Yogi2 said:**
> 

If I can't uninstall Grub, is it possible to change the default OS on it's menu to something other (Vista in my case) than Ubuntu?

see [here]("https://help.ubuntu.com/community/Grub2")

---

### Post by Yogi2 on 2009-11-03
[presence1960]("http://ubuntuforums.org/member.php?u=657448"): good question!  

Windows currently is my main OS.  I rarely used Fedora and only installed it to become familiar with Linux in general.  Thus 99.9% of the time I was booting into Windows.  All I had to do is turn on the power and Windows came up.

Using Grub forces me to hit [ENTER] or wait for whatever the default timeout is.   I understand that's a small price to pay unless I have to reboot my computer several times to get Windows to function properly (the reason I'm considering migrating to Linux instead of upgrading Windows).  

Grub just adds another layer of complexity to booting my system, albeit small.  If I can get by without it, I prefer to do that at this point in time.

---

### Post by achron on 2009-11-03
Sooo, could you not boot into Ubuntu and change the Grub default OS to Windows, and the timeout to 1 second?  Seems like the tiniest delay and the minimal risk solution.  When you want Ubuntu, you have to pay attention, but defaulting to Windows will take 1 more second. Sure beats hanging around pinging Delete to get the BIOS to pop up.

---

### Post by Yogi2 on 2009-11-03
OK, I'm getting the impression that Grub is permanent once it's installed.  That's a shame given the fact I may decide to stick with Windows if I can't get Ubuntu to perform to my liking.  ;)

Changing the boot order seems like the best approach.  This is my first excursion into the bowels of any Linux OS, thus I'm a little hesitant to edit system files.  After reading some of the documentation on the subject, it looks like just getting the StartUp Manager installed is a trick and a half.  I'll be trying my luck at editing a little later in the day.  So, if you never hear from me again because I can't boot any OS, thanks for all the suggestions so far.

---

