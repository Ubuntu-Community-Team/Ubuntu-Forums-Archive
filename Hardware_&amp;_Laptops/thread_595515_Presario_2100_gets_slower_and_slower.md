---
title: "Presario 2100 gets slower and slower"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by Canada3332 on 2007-10-28
Hi all,


I recently installed Gusty Gibson, otherwise known as 7.10 on a Compaq Presario 2100 I had laying around. I had installed Gentoo on it before, and except for audio, everything was functioning normally. I have no built-in wireless on this, but instead use a Atheros based wireless card (PCMCIA.) 

No complaints about the installation, it couldn't have been easier. What troubles me is after the installation. For starters, the system takes a **LONG** time to boot. We're talking 2 to 3 minutes here. Now, I know that linux takes longer than other operating systems to boot, with all the services it has to start and the like, but that's just getting up there. 

After the system boots it's nice and speedy, using all 256MB of RAM and about 32MB of the 1GB of swap I have. Still, no problems with performance or anything like that. Then, after about 15 minutes of doing something, or nothing, the system will start to get slower. I'm talking **really** slow, like it's swapping a lot, and yet top and the hard drive disagree with this diagnosis. Think of what a computer does when it's swapping a LOT. Windows that were previously open take a while to disappear, and new applications take forever to start, or just plain don't. This is what the system does. Yes, I've quit all other applications. The only thing I'm running 99% of the time is a terminal. I've killed all the services that I'm not immediately using, with the exception of ssh, and I've moved it closer to the wireless access point. No difference. 

The cursor moves, but the menus are dead (won't even come up) and I can't kill X. I can type in the terminal, but I get no result... in the end, I always end up having to do a hard reset.

Never had these problems running Gentoo.

Is anyone else experiencing problems similar to mine?

I'm not looking to start an OS flame war here, I'd just like to get this problem resolved. I've already explained my reasons for switching from Gentoo to Ubuntu, let's just leave it at that. Thanks.

---

### Post by jetpeach on 2007-12-08
you've probably long since given up on Ubuntu on your Presario 2100. I have the same laptop and have been using ubuntu on it since 6.06 and haven't yet the problems you have. i am now on gutsy.
problems i do have though are suspend/hibernate and getting graphics to work accellerated was a pain, but it is *sorta* done now...

---

### Post by Voltxion on 2007-12-24
Well I just decided to pull mylaptop out of storage (my parents had it for a good 3 years) so I decided I would install ubuntu 7.10 on it, I poped in the desktop CD and it loaded very slowly to get to even the icons on the live CD, then I clicked install about 45 minutes ago the laptop is still loading the install stuff... I have yet to see anything visual happen on screen but all the lights are blinking and the cd is doing stuff i can feel it vibrating.... 

any suggestions? should I format the HD before I try to even boot linux on it, I thought I would just format and partition it during installation. 

Also I have a older computer I installed 7.10 on that I had to install using safe mode graphics, I didnt restart this because I didnt have a issue loading the live cd just the time it took, could I need to load it in safemode?

---

### Post by Scott S. on 2007-12-24
I suggest waiting it out. I was playing with a few OS's before I settled on 7.10 and I noticed that ALL of them installed very slowly from the CD drive but flew like lightning from the DVD drive... a newer, faster drive.

This tracks with the live CD taking a long time too. It's not the box itself, it's the slow drive. Let it work through and then judge by how it runs off the HD. Mine is quite fast, much faster than XP on the same box and faster than Suse 10.3 too.

Once up, Gnome is a little slow but ok... I'm running E DR16 on it's own (no Gnome or KDE) and she flies even on this older box (Athlon XP2000+ with 2G ram and an old 256MB PCI video card... yea, PCI !!!)

I was forced to experiment when my main box, a Sempron 4000 on a Winfast mainboard, blew out the AGP and on board graphics both... silly thing won't even show a display with the PCI card but runs otherwise. I cobbled this set together to have a machine while I save up for a dual core or AMD64.

EDIT: The OP must have had a mem leak in a driver somewhere... it's the only reason I can think of for those symptoms.

Scott

---

### Post by Voltxion on 2007-12-24
Well still having no luck getting it installed, It keeps hanging and not doing anything after I click on the install Icon.... I tested my computers memory I tested the CD on two other computers, it worked on both booted up, can I make a portable HD boot the install and run it from there? I don't know if that is fast than the CDrom seeing as its USB1 not 2

---

### Post by xeth_delta on 2007-12-24
> **Voltxion said:**
> Well still having no luck getting it installed, It keeps hanging and not doing anything after I click on the install Icon.... I tested my computers memory I tested the CD on two other computers, it worked on both booted up, can I make a portable HD boot the install and run it from there? I don't know if that is fast than the CDrom seeing as its USB1 not 2

What speed did you use to burn the CD? High speeds often cause installation problems on certain optical drives.

---

### Post by Voltxion on 2007-12-24
I made it at 2x I usually try to burn at the lowest possible speed, seeing as when I was younger I thought it would be a good idea to burn everything at max and then I had a lot of coasters I still use in college today lol

---

### Post by xeth_delta on 2007-12-24
> **Scott S. said:**
> EDIT: The OP must have had a mem leak in a driver somewhere... it's the only reason I can think of for those symptoms.


It could very well have been that. For what it's worth, my computer has an Atheros wireless card and I have the madwifi drivers installed. Previous versions of the drivers (I think they already solved it) had a bug, that after certain time, will cause some "rx FIFO overrun; resetting" errors. If a workaround was not used, whenever the errors were present,  the system will be slowed down. On a recent computer something like that would not be that obvious (it was most noticeable in the beryl animations), but on an old system, the story would probably be quite different.

That said, updating the **locate** database can also slow down the system for a couple of minutes. I have noticed it runs once every day, at least it does it that often on my system.

Xeth

---

### Post by xeth_delta on 2007-12-24
> **Voltxion said:**
> I made it at 2x I usually try to burn at the lowest possible speed, seeing as when I was younger I thought it would be a good idea to burn everything at max and then I had a lot of coasters I still use in college today lol

Have you tried installing from the "alternate installation CD"?

[EDIT]: The alternate CD does not use the graphical interface to perform the installation process, which is used by the normal desktop CD.

---

### Post by Voltxion on 2007-12-24
I have tested 2 CDs for 7.10 and one 7.06 disk I had from a while back, I have ran teh CD integrity check on all 3, and I have a crap tower, that I use to test things on... hardware etc... and all 3 CDs install successfully on the desktop tower..

EDIT : I got an error telling me to upgrade my bio or use force_addresx then some numbers. I wasnt quick enough writing it down, this is while it loads the live CD

---

### Post by xeth_delta on 2007-12-24
> **Voltxion said:**
> I have tested 2 CDs for 7.10 and one 7.06 disk I had from a while back, I have ran teh CD integrity check on all 3, and I have a crap tower, that I use to test things on... hardware etc... and all 3 CDs install successfully on the desktop tower..

EDIT : I got an error telling me to upgrade my bio or use force_addresx then some numbers. I wasnt quick enough writing it down, this is while it loads the live CD

Sorry for asking again. Were any of those CDs an "alternate installation CD" (they don't use the regular graphical installation process): [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download"), below the "Start Download" button.

Sometimes the regular installation CDs have issues on certain hardware configurations.

---

### Post by Voltxion on 2007-12-24
No I did not I will attempt using one

---

### Post by xeth_delta on 2007-12-24
> **Voltxion said:**
> No I did not I will attempt using one

Slightly off topic, I just noticed that "alternate  CD" might have generated some confiusion, as it could also have meant "a different CD". Sorry about that, I'll clarify the post so that eventual future readers will know what I meant. :)

Back to the topic, give the CD a try, and let us know how it goes.

---

### Post by Voltxion on 2007-12-25
Well the install is actually running with teh alt CD, thank you. Now I was wondering what I could do with the system to make it run more efficiently, I  just plan to cut out alot of the "fluff" like taking out compiz and that stuff. or any threads that someone can point me to? I am slightly new to linux, I can setup a server thats about it.

---

### Post by xeth_delta on 2007-12-25
> **Voltxion said:**
> Well the install is actually running with teh alt CD, thank you. Now I was wondering what I could do with the system to make it run more efficiently, I  just plan to cut out alot of the "fluff" like taking out compiz and that stuff. or any threads that someone can point me to? I am slightly new to linux, I can setup a server thats about it.

You're welcome. Maybe using a light graphic interface, such as xfce (as xubuntu uses), fluxbox (as fluxbuntu [www.fluxbuntu.org]("www.fluxbuntu.org") does), etc.

I suppose you could install the desktops with the packages xubuntu-desktop and fluxbox.

---

### Post by thumbmaster021 on 2008-01-05
Now back to the original post, I am now working on a Presario 2100.  I have none of the problems you describe other than the 3:20 boot time, which is extremely annoying.  As with the freezing after 15 min I have no idea.  I am running my laptop with Ethernet, I got 3D acceleration out of the box, and have been having no problems other than the long boot up.

By the way, i am running Ubuntu 7.10 from a clean install and have 512 RAM installed in mine.

---

### Post by ReverendShaft on 2008-01-05
I've been trying to install 7.10 on my recently resurrected Presario 2100 as well, and have the same installation trouble -- I think I started the install process about an hour ago, and just got past the language selection (the first dialog).

Just an FYI: This is not a CD issue.  I thought the same thing, so I moved everything over to a USB pen drive, but the installation problems persist.  An issue I've come across in prior installs was power management, so I used the noacpi boot switch as well.  Still, no dice.

I'm downloading the alternate install CD now, but I fear that this UI issue will remain present after installation.

---

