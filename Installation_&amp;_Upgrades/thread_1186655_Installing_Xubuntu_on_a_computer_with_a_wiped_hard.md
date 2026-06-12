---
title: "Installing Xubuntu on a computer with a wiped hard drive."
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by prions on 2009-06-13
I got an old computer recently, and wanted to install Xubuntu on it. 

So, I wiped the hard drive of everything, then burned the latest version of Xubuntu onto a CD Rom from my laptop. 

But, when I put the disk into the desktop, all it says is "Invalid System Disk".

---

### Post by merlinus on 2009-06-13
Do a checksum on your .iso and burn at no more than 4x speed, if possible.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The other possibility is that your computer's bios is not set to boot from the cd first.

---

### Post by prions on 2009-06-13
I wiped windows off that computer. And I put Xubuntu onto the cd with ISO Recorder.

I'm pretty sure I downloaded it right. It works when I put it into my laptop with XP.


](*,)](*,)

---

### Post by prions on 2009-06-13
Anyone?

---

### Post by tommcd on 2009-06-13
First, you need to do what Merlin said in post #2:
1. When the Ubuntu CD boots, choose the option "check disc for defects". This will take a while. If it passes, the disc is good.

2. If you can not boot from the Ubuntu CD, and instead just get the "Invalid System Disk" message, then go into the computers BIOS and make sure the computer is set to boot from the cdrom as the first boot device.

---

### Post by merlinus on 2009-06-13
Did you check that your computer is set up to boot from the cd drive before the hdd?

---

### Post by prions on 2009-06-13
How can I get to BIOS? Nothing seems to work on it now that the hard drive is totally wiped.

And when I boot the Xubuntu cd, there is no option to check the cd.

---

### Post by merlinus on 2009-06-13
Generally you press one of the F keys just after starting the computer, and on some Del is the one.  You may be able to google your computer model and find out, if you no longer have the original docs.

Try F4 first, though.

---

### Post by prions on 2009-06-13
Nothing worked. Probably was a bad idea removing windows 98 from it. 

Maybe I could find a windows 98/xp disk somewhere and just boot that. Then run the Xubuntu CD. 

Any key I press just gives me the same message.


Edit: I held on control and it just gave me some information, no bios.

---

### Post by raymondh on 2009-06-13
Hello,

This link  may help (to access the BIOS)

[http://michaelstevenstech.com/bios_manufacturer.htm](http://michaelstevenstech.com/bios_manufacturer.htm)

Regards,

---

### Post by prions on 2009-06-13
Its f2. 

Let me have a look around now.

Edit: GOT IT!

Thanks guys. :)

Edit #2: If I have a problem installing I'll just post it here.

---

### Post by raymondh on 2009-06-13
@ merlin ... good work on the joyneo04 thread

---

### Post by prions on 2009-06-13
When the hard drive was partitioning, it might have froze. 

Its been a half hour and no progress.

Should I restart the computer or wait some more?

---

### Post by AllenGG on 2009-06-13
Waiting more than  3 or 4 minutes is futile. Example, took a new fresh harddrive, loaded 8.10 and from turning on the machine, loading, following the install instructions to getting on the internet, total time 12 minutes.   Added all the fluff later.               :cool:

---

### Post by prions on 2009-06-13
But this computer is very old. 128 mb ram and about 20gigs hdd. ;)

---

### Post by prions on 2009-06-13
Ok I'm past that. But once I got to the name registering part, my keyboard wouldn't work.

---

### Post by prions on 2009-06-13
The keyboard works fine except at step 5.

---

### Post by wpshooter on 2009-06-13
> **prions said:**
> The keyboard works fine except at step 5.

Have you checked the hardware requirements for installing Xubuntu.

Xubuntu can be installed on older equipment BUT 128mb of RAM "MAY" be to little even for Xubuntu !!!

P.S. - You probably need to attempt to do the Xubuntu installation from the ALTERNATE (text based) CD version of Xubuntu instead of the live/desktop CD version.

---

### Post by prions on 2009-06-13
I did check the requirements. 


Where can I get it the text based cd? I cant find it on [http://www.xubuntu.org/get](http://www.xubuntu.org/get). 

Should I just switch to DSL? :/

Also, I tested the memory and it was ok. My disk is fine too.

---

### Post by raymondh on 2009-06-13
> **wpshooter said:**
> Have you checked the hardware requirements for installing Xubuntu.

Xubuntu can be installed on older equipment BUT 128mb of RAM "MAY" be to little even for Xubuntu !!!

P.S. - You probably need to attempt to do the Xubuntu installation from the ALTERNATE (text based) CD version of Xubuntu instead of the live/desktop CD version.


+1 on the alternate install

Here you go

[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/9.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/9.04/release/)

Good luck.

---

### Post by raymondh on 2009-06-13
also, have a look at the Xubuntu notes

Xubuntu releases:

    * 9.04, codename Jaunty Jackalope (newest stable release).
    * 8.04.1, codename Hardy Heron, includes Long Term Support.

Minimum system requirements
You need 192 MB RAM to run the Live CD or 128 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time. To install Xubuntu, you need 1.5 GB of free space on your hard disk. **Once installed, Xubuntu can run with starting from 192 (or even just 128) MB RAM, but it is strongly recommended to have at least 256 MB RAM.**

---

### Post by prions on 2009-06-14
The alternate install worked a lot better. 

Xubuntu is working very smoothly on the computer, I just need an internet cable to run from my laptop to desktop. 

Cheers, gentlemen.  =D>

---

### Post by merlinus on 2009-06-14
Excellent news! Good on you for persevering....

@Raymond
Thanks for the compliment on the joyneo04 thread, Raymond.  It is obviously not yet solved, but at least the guy feels supported by the community.  And he certainly refuses to give up!

---

