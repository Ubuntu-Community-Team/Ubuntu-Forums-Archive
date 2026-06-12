---
title: "installaton freezes"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by Zombie Socrates on 2009-05-20
Hi, and thanks for reading my post. I'm a extreme novice who recenetly decided to give linux a try. I've been trying to get ubuntu 9.04 installed for 2 days now with no success. When I run the installation through the live CD I get as far as copying system files, at which point the computer freezes up (mouse won't move, progress bar freezes, not HD activity). This usually occurs between 22 - 29%. I've also tried using the alternative install CD with similar results. After several attempts I decided to try a different distribution. So far I've tried Fedora 8 and 10, Debian 5, and Suse 11.1. All of them freeze at various points in the installation. Any ideas on what might be causing the problem? System information follows:

Via k7-ms8157e 
AMD athlon XP 2400+ 
1024 RAM
ATI Radeon 

Thanks in advance for any help!

---

### Post by Zombie Socrates on 2009-05-20
Ok, I can add 8.04 to the list of failed attempts. Installation froze at copying files, 23% and 24% on two respective attempts. 

I tried installing ubuntu 9.04 on an old laptop and it went off without a hitch, so my guess is something about my other system is causing the install to fail. The problem is I can't figure out what that something is. Thanks again for any help you  can provide.

---

### Post by albinootje on 2009-05-20
> **Zombie Socrates said:**
>  I tried installing ubuntu 9.04 on an old laptop and it went off without a hitch, so my guess is something about my other system is causing the install to fail. 

I assume you burned the installations cdroms at low speed, and you verified them with md5sum ?

Try and find out whether that specific machine needs extra boot parameters. I usually try "noapic nolapic" first when a machine or an installation gives trouble. 
And as an example, at work there's a machine which needs "irqpoll" as boot parameter otherwise it won't even boot properly.

See here :
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Zombie Socrates on 2009-05-20
Thanks. I did burn all of them on the lowest speed and I've checked the discs, so I don't think that's the problem. I also successfully installed 9.04 on a different computer, so I know for sure that at least that disk works. 
 
Thansk for pointing me in the direction of the boot options. I'm very new at this so it's a process of trial and error for me, but it definitely gives me something to work with (and a trial by fire is a great way to get started learning!). I tried installing 9.04 with the "noapic nolapic irqpoll" options, but it froze again. I had to run to work  so I wasn't able to try much, but I'll start trying differnt combinations later to see if one works. Like I said, I'm very new to this, though, so are their any options (other than the one's you've already suggested) that you think might be particularly useful? Thanks again for your help.

---

### Post by albinootje on 2009-05-20
> **Zombie Socrates said:**
>  I tried installing 9.04 with the "noapic nolapic irqpoll" options, but it froze again. I had to run to work  so I wasn't able to try much, but I'll start trying differnt combinations later to see if one works. 

Excellent.

Please try with the "noapic nolapic" options first, and try not to mix those options too soon ("noapic nolapic" is a standard exception).

Also before you do the installation, please do the following a terminal :
```

dmesg > ~/Desktop/dmesg.txt

```
And copy or emails that dmesg.txt file to yourself.
The command dmesg can show you possible irq conflict messages, or 
BIOS bug remarks. You might want to attach that text file here, so that everyone else can have a look at it. Sometimes there are even suggestions (found with "dmesg") like "irq 10, didn't care, please try with irqpoll option", things like that.

And then before starting the installation, do the following in a terminal :
```

tail -f /var/log/syslog

```
and make sure that the output of that stays visible during the installation.
Hopefully the moment it freezes you can see some useful output on it.

---

### Post by RichFellows on 2009-05-20
Try pulling and reseating your RAM.  Do the same for the hard drive cables.  Sounds silly but let's try the basic stuff first.

---

### Post by Zombie Socrates on 2009-05-21
Thanks for the suggestions. I reseated my memory and made sure my hard disks were securely connected.

I ran the terminal commands you suggested, albinootje. I'm looking through it myself, though I'm not sure I'll be able recognize much that would be useful, and I've attached the file as well in case anyone else would be willing to look through it. 

I also kept the system log open during an install attempt (both with the noapic/nolapic options and a normal install). The same text appeared immediately before the crash on both attempts:

ubuntu python: not copying bin/keyctl
ubuntu python: not copying etc/casper.conf
ubuntu python: not copying etc/request-key.conf
ubuntu python: not copying etc/initid/casper
ubuntu python: not copying lib/libhandle.so.1.0.3

I'll keep trying boot options to see if I can get it going, but I wanted to post the information I had so far. Thanks again for all the help.

---

### Post by albinootje on 2009-05-21
> **Zombie Socrates said:**
> I've attached the file as well in case anyone else would be willing to look through it. 

Good, thanks.

I was wondering.. you're installing Ubuntu on the 20 Gb disks ?
Could you run a bad block test on that ?

You can do that as following from a terminal, in the live session of the Ubuntu installation cdrom :
```

sudo badblocks -vv /dev/sda

```

Another idea I wondered about, does the system freeze each time at the same point of the installation ?
Or is that more after a certain amount of time ? Like 10 minutes each time, or 15 minutes ?

Can you run the "live session" (Try without making changes), and then -not- install, but just use it to browse the internet for, say, 15 minutes, and see how that goes ?

---

