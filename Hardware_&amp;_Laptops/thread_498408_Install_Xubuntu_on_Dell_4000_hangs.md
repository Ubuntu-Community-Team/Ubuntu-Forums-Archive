---
title: "Install Xubuntu on Dell 4000 hangs"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by ArtDeco on 2007-07-11
Trying to install xunbuntu 7 on an older Dell Inspirion 4000 laptop w/only 128mb ram, 10 gig disk as a dual boot win2k / ubuntu system. 

On my third try so far - first with a CD packed with Ubuntu linux bible that hung at a solid white screen, second with an ISO downloaded from MadTux that wouldn't boot, this time with the new internet based installer (wubly ?) that doesn't require partioning the hard disk (very cool if it works) . 

Afer rebooting into ubuntu, the Installer seems to hang at configuring language-pack-en-base. Status bar shows 1% for several hours so far. No sure if I should let it go all day or if it's really hung up.

I googled 'language-pack-en-base' and found several references in the forums but I don't know enough to tell if they were ever resolved and if so how ?

Any help appreciated.

---

### Post by ugm6hr on 2007-07-11
Is there a reason you haven't tried an official Xubuntu?
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

Get the AlternateCD for that hardware.

If you are planning on dual-booting, I would recommend creating an empty space on your hard drive with GParted LiveCD first: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by ArtDeco on 2007-07-11
Unlike the rest of Ubuntu's stuff , Xbuntu does not have a live CD available through shipit, and I don't trust the download and burn an ISO approach on my machines since not one of the three I downloaded from madtux and burned actutally booted correctly. 

Besides the advantage of the wubi approach is that disk partioning isn't suppossed to be necessary . Very cool if it works.

Thanks for the link to gtparted.  I will partion the drive and reinstall if  if necessary but I now have a good ISO on my hard disk and would like to use it if possible.

---

### Post by ArtDeco on 2007-07-12
I now have a good ISO of xUbuntu 7 alternate CD on my windows drive and some windows readable log files from the LUPIN installer. Maybe I can see where it died?

I suspect but cannot  yet prove that most combinations of Dell's laptops and linux are a fight to the finish to get installed and that is why Dell charges more for a laptop with Ubuntu than an identical one with windows. Sad.

---

### Post by ugm6hr on 2007-07-12
> **ArtDeco said:**
> I suspect but cannot  yet prove that most combinations of Dell's laptops and linux are a fight to the finish to get installed

Depends on which model and hardware therein. I had no great difficulties with an old Dell5000e or a Dell500m laptop.

I appreciate that wubi sounds good - but with relatively limited hardware (128MB RAM) it will be a struggle to install any way apart from booting directly from the Xubuntu AlternateCD.

So if you are serious about installing Xubuntu, then I would suggest you try my previous recommendation:
GParted LiveCD to repartition - assuming you have a single Windows partition - just shrink it down, and leave an empty space for Xubuntu (of at least 2.5GB).

Then boot from the Xubuntu AlternateCD and chose the Automatically Partition the Free Space option (or something like that) during the install process.

---

### Post by ArtDeco on 2007-07-12
Yeah, I think you are right. I also ordered more memory - adding a quarter gig stick to bring it up to 320mb  has to help. I am serious about making this a linix system because Win2k is due to go off the supported list soon; however, I am not in a huge hurry because I still have other machines available.

---

### Post by ugm6hr on 2007-07-12
The extra RAM will make a huge difference.  You will have the option of using a LiveCD to install too.

I personally prefer Xubuntu, but Ubuntu is a little easier to use without modification...

---

### Post by ArtDeco on 2007-07-12
I like the look of xfce pretty well too. I am a linux newbe but especially on a laptop I think I prefer a stripped down system w/ abiword and gnumeric ( i use the windows versions)  instead gnome and office, but I will take whatever runs, I guess.

I am searching for the documentation for the alternate cd install but I can't find it - got this message:
The requested URL /ubuntu/dists/edgy/main/installer-i386/current/doc/ was not found on this server.
Any body know where the manual went?

---

### Post by ugm6hr on 2007-07-12
The alternateCD install is described in this:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

It specifically talks about dual-booting, if that's what you're planning.  If not - just choose to use the use the whole drive option.

To be honest, I don't think you will need documentation to install it.  Make sure anything of importance is backed up if necessary, before repartitioning.

If you are planning a dual-boot - I would still recommend using GParted to repartition first.

As for the Xubuntu / Ubuntu debate - everyone has their own opinion.  If you want to add wifi / multimedia keys / larger apps (e.g. OpenOffice) / battery monitor / volume control etc to Xubuntu it's pretty easy when you know how.  And if you don't know how - you know a man (or forum) that does :)

---

### Post by ArtDeco on 2007-07-13
Cool. Did the Uninstall thing, downloaded GParted, and now am waiting on RAM sticks  to arrive- weeks pass -I am in Amish country - Gods country  because no one else wanted it-  and things are REALLY slow here. But Thanks A Lot Ugm6hr. This will work out OK. Also thanks to AGO in the WUBI forum ( if you are reading this (or not)) . You  guys are the reason for not just going along with the MS plan for world domination.

---

### Post by ArtDeco on 2007-07-14
Installation of Xunbuntu via Wubi on ancient Dell laptop is complete in three easy steps

1)Ran uninstall of Wubi which deleted old files and backed up the good ISO.
2)I put an additional memory stick of 256mb of ram in the Dell 4000 for a total of 320mb.
3)Ran the Wubi install again. I asked me a couple questions, found the ISO, and chugged away for about an hour .

I now have a dual boot Win2K and Xunbuntu laptop without ever partioning the disk. Amazing what a $70 ram stick can do.

Next I'll decide if I can work out the kinks in the Dell - mouse pad, printer, digital camera, and such and just delete Windows - along with the 54 security patches they just sent me.

This thread can be closed.

---

### Post by ugm6hr on 2007-07-14
To give you a headstart on the touchpad issue:
[http://ubuntuforums.org/showthread.php?t=492984](http://ubuntuforums.org/showthread.php?t=492984)

Good luck.

---

### Post by ArtDeco on 2007-07-20
just an update on wubi xunbuntu unbuntu and too much software on an old laptop.

I had little joy with xunbuntu;  it works but is flaky ; mouse jumps, menus hang, screen flickers, etc. probably all fixable but since unbuntu works smoothly although slowly I used wubi to remove xunbuntu and install unbuntu . Removed Open Office , Gimp, and Evolution on the linux side and MS Office, Outlook, and Explorer on the Microsoft side and installed a minimum Gnome Office on both with Synaptics and Add Remove Programs respectively. I use notenab HTML editor on microsoft  and just installed Bluefish HTML editor on unbuntu .

Trying to figure out how to cross the great divide - Save in Linux, Open in Windows,  Copy in Windows, Paste in linux, etc. Interesting possibilities of messing up whole system eh?

I wonder if I can run windows defrag without screwing up wubi? I may try it or just do the uninstall/reinstall thing yet again for kunbuntu next week when I have some time.

---

