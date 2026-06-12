---
title: "Ubuntu 9.04 on Compaq Laptop (Evo n400c)"
date: 2010-02-24
forum: Hardware
---

### Post by michael2009 on 2010-02-24
Hello there, I started this thread because I need specific advice on this hardware that I cannot seem to find anywhere else on this forum. 

I am a Linux newbie, Ubuntu works ok with my laptop, together with Windows XP sp3 installed on the first partition but it is not as fast as windows XP used to be (before I installed Ubuntu on the other partition). I want it to work faster.

 I have tried to keep a slim installation, using around 4-5GB on the Ubuntu partition. Disk Usage Analyzer lists 12.9 GB used space out of a total capacity of 36.4GB. The partition containing windows (listed as /windows in Ubuntu's file system) accounts for around 6GB of that used space. Ubuntu's System Monitor shows an average of around 58% of memory used by programs, with 37% in use by the cache, that's without running any user programs apart from the Monitor.

CPU: Pentium III (Coppermine) 850 Mhz 
Memory: 244.8 MiB
Hard Disk: 40 GB (Windows Partition 18 GB; Ubuntu Partition 21 GB)

Would Ubuntu run faster if I deleted the Windows OS? Or can I upgrade the memory to 500 MB to speed things up? 

Is it also possible to upgrade this machine by installing a new processor, like Pentium 4 for example, to make it faster and better?

---

### Post by IcarusR on 2010-02-24
Deleting windows will not affect ubuntu speed.
Increasing amount of ram always improves a system.
CPU is soldered into its socket (lots of small connections close together) so would have to be done by someone who knows what they are doing. 
Not really worth paying to have this done.

I had an Armada 700 (same CPU ??) with 1gb ram with ubuntu installed, it ran well.

---

### Post by michael2009 on 2010-02-24
OK thx very much for that very useful information. I have never installed RAM before, is it possible for an experienced DIY-er? umm.. and where could I buy it in the first place?

---

### Post by michael2009 on 2010-02-27
I hope I do not offend any loyal Ubuntu fans out there. I think Ubuntu is great, and has a excellent record for development of a user friendly Debian-based Linux OS. 

The problem is I do not see any reasons why I should upgrade my laptop just to get a reasonable speed that matches with the speed of XP sp3 on this same piece of hardware. 

I had a very nimble Debian OS installed for a short time last year, the only problem was adding programs without a decent internet connection. 

Is there anyone out there who can recommend a Linux based OS, or OS version, that will fit nice and snug with a Pentium III processor, 244 MiB RAM, and a 40 GB hard disk, i.e. a really compatible distro?

What about PC Linux OS, how does it compare for speed on an old laptop?

---

### Post by kerry_s on 2010-02-27
i'm running debian lxde on 450mhz 256mb ram, you can give that a try.

grab the net installer, that means you need to be connected to install.

[http://cdimage.debian.org/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-businesscard.iso)

go into the advanced menu> alternate desktops> lxde

i'll put a pic in a bit, i share it with my niece, so it's setup to be simple for her. yours will look no where near mine, but it's that tweakable.

---

### Post by michael2009 on 2010-02-27
thanks for the recommendation. Never heard of lxde, does it come with a software bundle, like Open Office, Firefox, media players etc?

---

### Post by kerry_s on 2010-02-27
> **michael2009 said:**
> thanks for the recommendation. Never heard of lxde, does it come with a software bundle, like Open Office, Firefox, media players etc?

it does come with open office & iceweasl, media player you'll have to install what ever you want. debian lxde is fairly bare bones, they leave it up to the user to choose what you want. the first thing i grabbed was synaptic, a graphical package installer(su && apt-get install synaptic). i use the expert install mode, so i could choose to have a sudo system, root is locked on mine.

on second thought debian might be a little rough if your still to new. you asked about pclinuxos, they also have a lxde version that should be more beginner friendly for you to learn.

[http://www.pclinuxonline.com/?p=174](http://www.pclinuxonline.com/?p=174)

---

### Post by michael2009 on 2010-02-27
> **kerry_s said:**
> on second thought debian might be a little rough if your still to new. you asked about pclinuxos, they also have a lxde version that should be more beginner friendly for you to learn.

[http://www.pclinuxonline.com/?p=174](http://www.pclinuxonline.com/?p=174)

I just checked out the pc linux lxde web page. Not much information there. I am not clear what are the actual differences from the main PC Linux OS distro, is it just a simpler version or what? Anyway I downloaded the debian lxde distro from your link. I shall try it out when I have time, and leave Ubuntu as my main OS for now. Thanks.

---

### Post by kerry_s on 2010-02-27
> **michael2009 said:**
> I just checked out the pc linux lxde web page. Not much information there. I am not clear what are the actual differences from the main PC Linux OS distro, is it just a simpler version or what? Anyway I downloaded the debian lxde distro from your link. I shall try it out when I have time, and leave Ubuntu as my main OS for now. Thanks.

there are 4 main desktops in linux.

kde = heaviest works best with at least 1ghz 1gb ram
gnome = medium works best with at least 1ghz 512mb ram
xfce4 = lite works best with at least 500mhz 256mb ram
lxde = lightest works best with at least 300mhz 128mb ram

pclinuxos main uses kde
ubuntu main uses gnome

the difference between debian & pclinuxos is debian you have to install, no live cd. pclinuxos is a livecd & more complete, you can use it with out having to install first.

it's all a matter of taste, how things feel to you. i'm a debian person, i try others but always come back to debian or a debian based linux. you'll just have to hop around till you find your place, we all do it till we find what just fells good using it. i know debian like the back of my hand so it comes easy.

i'm using ubuntu 9.04 on my main desktop, just installed 2 days ago removed windows 7, haven't even bothered to change much just made it usable enough for me for now, i don't keep a keyboard plugged in, so the first thing i did was set that up. i like it a certain way so i had to do a script to toggle it from the icon.

---

### Post by michael2009 on 2010-02-28
Thank you Kerry s, that was really valuable information. I shall post again when I get around to installing lxde, and let you know how I got on with it. :)

---

### Post by frncz on 2010-02-28
Hi

I have a Compaq Evo N400c, now running Ubuntu Lucid 10.04. I increased the memory to 384 Mb which I think is the most you can put in there (unfortunately) and changed the hard disk to a 160 Gb. Both these operations are relatively easy to do, and well worth it.
It runs fine with the standard Ubuntu distribution. It ran fine with Hardy as well. The lack of memory is perhaps the most serious limitation, but the light weight laptop is great for travelling. The fact that it is old also means that I would not lose too much if I lost it, dropped it or if it was stolen.
The screen is a bit dark - I don't know if it is because it is old, or because I am not using a setting to brighten it up. I also purchased a new battery, which gives me about 90 minutes.

---

### Post by michael2009 on 2010-03-01
I have been out of the UK for over a year now, working abroad, and changed to Linux just a few months ago, so I do not know much about the options for upgrading in the UK. I agree that the compaq is great for travelling (I left the docking station at home in the UK, and bought myself an external CD/DVD drive, which is much lighter and gives me more flexibility). 

The computer shop that installed the 40 GB hard drive for me last year told me that was the maximum size available, because the newer and larger HDD's are all SATA, which are not compatible with the ATA drive system on the n400c. So I would really like to know how you managed to get a 160 Gb drive installed.:O

Re: the memory upgrade, I recently asked a shop for 512 Mb upgrade, and they reckoned it was possible, offering to install it for me, but I haven't had time to go back there yet. 

On a different topic, HP Compaq provide the Bluetooth Multiport Module for wireless networking, but the shops I have been to tell me this is no longer available and repalced by USB modems, which I do not want. Have you, or anyone on this forum, used the bluetooth with the n400c?

---

### Post by frncz on 2010-03-02
I can't remember where I got the hard disk from. Are you sure the disk is ATA and not SATA? Both are available:
ATA: WD1600BEVE Western Digital 160GB capacity
SATA: WD1600BEVT Western Digital Scorpio 160GB capacity

For WiFi, I use a pcmcia card which is inexpensive, works fine and was immediately recognised by 10.04. However I had an older card that was not recognised by 9.10.

---

### Post by michael2009 on 2010-03-03
> **frncz said:**
> I can't remember where I got the hard disk from. Are you sure the disk is ATA and not SATA? Both are available:
ATA: WD1600BEVE Western Digital 160GB capacity
SATA: WD1600BEVT Western Digital Scorpio 160GB capacity


Mine's definitely ATA

---

### Post by davidvolvox on 2010-04-11
To add my experience.. old Evo N600C 370MB P3 1200MHz wifi via D-link PCMIA card runs 9.04 beautifully but 9.10 I couldn't get to run at all just reported disk errors.  I am wondering if 10.04 is worth trying or is this hardware just too old?

---

### Post by frncz on 2010-05-05
10.04 is definitely worth trying. It works fine for me. Problems with wifi ans PCMCIA cards under Karmic seem to have been resolved with Lucid. Mind you, I did change my Wifi card to get it to work under Karmic, before I upgraded to lucid.

The limited memory does mean it is a slow system, but it is stable and reliable, and fine for web, listening to music, office work etc...

---

### Post by Victor4156 on 2010-06-09
I have a Compaq N600c, but all the laptop power chargers in our house(I got the computer from my science teacher) are the wrong voltage. Until I get a power supply with the correct voltage, I'm going wonder arond these forums until i find a success that can help me before, during, and after I install, hopefully, Ubuntu 10.04

---

