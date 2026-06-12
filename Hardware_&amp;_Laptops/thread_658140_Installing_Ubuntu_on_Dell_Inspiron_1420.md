---
title: "Installing Ubuntu on Dell Inspiron 1420"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by pkpkpkpk on 2008-01-04
I bought a Dell Inspiron 1420 ( not the one that comes with Ubuntu pre-installed). This is more of a HowTo by a newbie

This one came with Vista Basic, which I promptly discarded ( **Can I get a refund for Vista? Please comment if you have any info on this.**

Anyways, for 3 days, I followed different posts on this forum and elsewhere to get the wireless working. It was a nightmare.

Actually the wireless solution is very simple and I wanted to document it here so that others who buy this laptop will be spared this nightmare.

=======================================
SETTING UP WIRELESS
=======================================

DO NOT INSTALL UBUNTU (THE REGULAR ONE)

Go to [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) and in the section  Dell OS Reinstallation 7.10 DVD ISO, burn the right iso based on your video card. This is huge (4 gigs) and needs a dvd

Reboot with dvd and choose to install ubuntu from this image.

After installation, update software sources to pick from restricted, multiverse, etc.
Then, go to restricted drivers manager, and add the broadcom drivers. It will  further download other stuff.

Since this image is a bit old, use Ubuntu's update manager to update to the latest code. 

Restart your machine and now, wireless works like a charm.

I still need to get the bluetooth and integrated web cam working (maybe it already is?) and will post here when I am done.

---

### Post by evil316 on 2008-01-04
I had asked about a refund for windows.  If the windows came with a prebuilit system the answer is NO you cannot get a refund.

---

### Post by igorlunamoura on 2008-01-23
Man, thanks a lot for the tip. I was trying to put my wirelles to work during like a month (okay...i just started using linux). Awesome what you did!! :)

---

### Post by frame45 on 2008-01-24
I am considering purchasing one of these Dell Inspiron 1420's. Would you recommend this? I am wanting to dual boot Ubuntu 7.10 & Vista, because I have some win only apps that I can't get around. 

Does everything work on the computer (ie Media shortcut buttons). After the install of this image. 

I looked at the wiki for the reinstall images and I looks like they have the table messed up it says Video Card and then File name. The nVidia 8400M GS says "ubuntu-dell-1420n-intelvideo-reinstall.iso" on the file name, and the Intel X3100 says "ubuntu-dell-1420n-nvidiavideo-reinstall.iso" I think those need to be swapped. 

Thanks for the Post if I decide to go with a Dell this will surely save me a ton of time configuring everything.

---

### Post by pkpkpkpk on 2008-01-24
Please check [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1420](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1420)

If you go with the NVidia card and the costlier wireless card, then everything works like a charm.

I still have not got my video card working to its full capacity.
I just dont have time now to play with it.

Other issues are:
Getting bluetooth to work
Getting the integrated camera to work.

I am hoping that someone will post abt it since this is a very popular laptop. On the other hand, you can try running your win-only apps using Wine.

---

