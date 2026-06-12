---
title: "Beginner worried about upgrade"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by peterkennett on 2009-10-21
I have a unusual problem and hope I can get some help with. I am a complete novice with Linux so I beg your patience.
 
I work in a highly secure office in which we have been given a PC with Ubuntu (V 7.04) installed. This PC is used just to play background music and I want to upgrade it to the latest vesion WITHOUT loosing any of the music on the hard drive.
 
Here's the kicker..
 
- The computer is not allowed to leave this secure office.
- It can not be attached to the Internet.
 
Is it possible to use a fresh install disk to overright the current OS so I don't loose the existing myusic files?
 
I wish to me able to play MP4 video files when I am done. I tried to simply install VLC but it wouldn't install on this older OS. 
 
Everything I do must be off-line. I can download files at home on my Mac and burn them to CD.
 
Is any of this possible?
What steps should I take?
 
Thank you!
 
Peter

---

### Post by howefield on 2009-10-21
All of that is possible.

But if its sole purpose in life is to play music, why would you want to upgrade it ?

PS. You should be able to play mp4 files on it without a full upgrade.

---

### Post by KhanTG on 2009-10-21
I agree to howefield.. it is doing the job that it is supposed to do (assuming without issue), leave it alone.

That being said; you DID say that it is in a "secure" situation, you really shouldn't mess with it unles ordered to by the BOSS.

---

### Post by peterkennett on 2009-10-21
I agree, I would rather NOT mess with a working system. I just can't get the mp4 videos to play. I am probably just missing the codecs but I haven't been able to find a way to install them on an off-line system. Do you have a good link I can use?
 
The files are .MP4 H.264 videos.
 
Thanks!
 
Peter
 
PS:  I am the boss.

---

### Post by KhanTG on 2009-10-21
did a quick troll of various sites.. don't know if this will work
but try looking [here]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").. this is a howto for feisty, using medibuntu (bunch of non-open-source or non-free software not normally included with Ubuntu)

---

### Post by gktaylor on 2009-10-21
Personally, I would install the operating system using the install disk rather than wrestling with older version of software. It is easier than searching for package dependencies in an off-line setting. When you reinstall from the bootable CD, make sure that you do not delete or reformat your Linux partition in the process. This should leave your file-system, and hence your music and videos intact. 

Backing up your music files on a removable hard drive first is a good idea. Good luck!

---

### Post by raymondh on 2009-10-21
Peter,

I've been looking at this (though they may be for hardy, intrepid and jaunty)

[http://www.ubuntugeek.com/how-to-install-multimedia-codecsadobe-flashjre-without-internet-connection-offline-in-ubuntu-810.html](http://www.ubuntugeek.com/how-to-install-multimedia-codecsadobe-flashjre-without-internet-connection-offline-in-ubuntu-810.html)

If you insist on upgrading versions .... I imagine I would be easier to just back up those files (or move them to a dedicated data partition)  and then install the newer version and move those files back to /home (or remount the data partition).

You could also do a root install which involves a 'manual' installation.

---

### Post by raymondh on 2009-10-21
> **gktaylor said:**
> make sure that you do not delete or reformat your [COLOR="Red"]Linux partition [/COLOR]in the process. This should leave your file-system, and hence your music and videos intact. 

You probably meant to mount but not format the current /home.

Cheers,

---

### Post by peterkennett on 2009-10-21
I like the idea of installing the latest version from a CD.  I downloaded the latest version from this website ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)) and burned it to a CD.  It just fit, and becamed named "disk 3" by my CD burning software.  Not sure where that name came from, but I didn't name it.     Are there disks 1, 2 or more that I should have received in the download?
 
Peter

---

### Post by gktaylor on 2009-10-21
I am not sure about the 'disk 3' label but I would recommend testing the disk out before heading to your off-line setting tomorrow. Try booting from the CD using your current computer. If you see the Ubuntu welcome screen then you created the CD correctly.

Good luck and have fun!

---

### Post by KhanTG on 2009-10-21
> **gktaylor said:**
> I am not sure about the 'disk 3' label but I would recommend testing the disk out before heading to your off-line setting tomorrow. Try booting from the CD using your current computer. If you see the Ubuntu welcome screen then you created the CD correctly.

Good luck and have fun!

don't forget to use the "Check disc for defects" option in the boot menu...

---

### Post by gktaylor on 2009-10-21
> **raymondhenson said:**
> You probably meant to mount but not format the current /home.

My (default) installation has only one data partition containing the entire root filesystem so I don't think that this comment applies. It would certainly work in a more complicated setup.

A quick web search confirms that the filesystem and existing data files are left mostly intact by the installer. That is, unless partitions are deleted and re-added by fdisk or the partition is formated.

Good luck!

---

### Post by peterkennett on 2009-10-21
It boots fine!  I even did the demo run (from the CD) and all applications seemed to be working well.  Now all I'll need are the quicktime codecs so we can watch the MP4 H.265 videos.  Anyone know where I can download those for an off-line install?
 
Thanks!
 
Peter

---

### Post by ubuntu27 on 2009-10-21
A new version of Ubuntu will be released next week, October 29. For half the world it will be for day 30 (TIme Zone differences).

I recommend you to wait for the new UBuntu Linux. 


What to do:


1) Back-up your data, that is your music and other important files into a portable device or to another hard drive.

2) Install Ubuntu 9.10 (Karmic) on your computer without the internet, AND also install it to another machine that is connected to the internet.

3) On the Ubuntu Karmic without Internet: 
 a) Open Synaptic Package Manager (System menu-->Administration-->Synaptic Package Manager)
 b) Search and select the packages that you will like to install (such as "ubuntu-restricted-extras")
 c) Go to File menu--->Generate Package Download Script
 d) Save it to a portable device such as USB Drive.

4) Go to your Ubuntu computer with Internet
5) Insert your portable device where you saved the script.
6) Run the Script
7) Save the downloaded files (deb files) to a portable device

8) Go to your Ubuntu computer without Internet
9) Install the deb files by double clicking

10) Enjoy.

---

### Post by peterkennett on 2009-10-21
Thanks 27.  I may do that this weekend.  The only other computers we all have are Macs.  Will 9.10 be available for Mac, and will the additional "extra" files I download on the Mac be compatible with a regular PC?
 
Second, if I install over the current version of Ubuntu, will all the files in my current HOME folder be left intact?  
 
Thanks!
 
Peter

---

### Post by peterkennett on 2009-10-22
Thanks to all that helped!  I installed Jaunty with no problems, after first creating a new partition and copying over all the music.  Worked great!

But then I  installed the Ubuntu-restricted-extras offline and VLC offline installers and discovered that the libqtgui4 and libqty-designer files didn't load, which then cascaded to many other dependent files.  After that partial install, my video player stopped working.  I am guessing that I needed to have installed all the Jaunty Updates first.. but without a direct Internet connection on this machine that didn't happen.

Any idea how I can install ALL the Jaunty updates offline?  I have to use a Mac at home to get the files and then put them on a thumbdrive.

Peter

---

### Post by jheaton5 on 2009-10-22
At the risk of stating the obvious, why didn't you just take it to IT or your Boss and tell them what you needed?  You can still do that.  Although they will probably go berserk over you using an unsecured disk in the thing.

---

### Post by KhanTG on 2009-10-22
I don't think that doing offline opdates would be very practicle.  if you look at the dependancies for the program that you want to install and just get them, you would also have to get the dependencies for them too, and so on and so forth...
 
 If all the machine does is play background music... and you're the boss (as you have proclaimed)... see if you can get it to an internet source for an hour or so and get everything you need in one stop.
 
 Have fun with that!

---

### Post by ubuntu27 on 2009-10-22
There is two things you can do.

1) Connect your computer temporarily to the Internet.
GNU/Linux is much secure than most of the Operating Systems. There shall be no problem connecting it to the Internet.

2) Create a Download Script for the package that you will like to install. I have written how to to that in my previous post.

  a) You can use the script to download, 
  b) or you can download it manually by opening the script with a Text Editor. 
     When you open the script with a Text Editor such as notepad or Gedit, you will see that there are URL or web address of each packages. You can use those URL to download from **any** computer that is connected to the internet.

---

### Post by peterkennett on 2009-10-23
I know it's hard to understand where I work...

The computer was purchased in a SECURE way from the USA and shipped by diplomatic courier to my office.  I can not have any computer in my office any other way, and I can never take this computer outside my vault or connect it the internet.  To do so would void it's security rating and it would have to be removed from my office and never brought back in.   I can not "hook it up just for a few minutes" to the Internet.  There is no internet connection in my vault.. at least not one the public uses.  My Internet connection is an INTRAnet not INTERnet.  It has no connection to the outside world, only classified networks I'd rather not discuss here.

Yes, I'm the boss, but I still have to follow rules set forth by my agency.  I can't break security.

While the computer is used NOW just for music, which it does just fine, I want to now play VIDEOS on it too.
That is why I am trying to upgrade it so it will play DIVX and/or MP4s.  

So now I have given up on making this thing work.  I wish they had given me a Mac, but I'm stuck with what they sent.  So now I will try and see if I figure out what format the movie player will play NATIVELY with no upgrades, and convert all my videos to that format.

Peter

---

### Post by GoldNugget on 2009-10-24
If your files are safely backed up on a separate partition, perhaps you should consider installing Linux Mint, which comes with the codecs pre-installed. It is based on Ubuntu so it should feel familiar.
[http://www.linuxmint.com/](http://www.linuxmint.com/) 

Good luck with your project.

---

