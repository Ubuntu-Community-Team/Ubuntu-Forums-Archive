---
title: "Thank you ATI !!!"
date: 2011-02-17
forum: Hardware
---

### Post by typhoon_tip on 2011-02-17
For all those with ATI graphic cards, big, huge improvement in the proprietary driver !! They fixed the slight tear of images that happened before (not sync with the vertical refresh all the times), and the graphic look now so smooth and brilliant, a huge thanks to them !! I have posted in their reported system about 2 months back about this issue, I guess they tackled it, bravo !

I suggest the ones who want to improve drastically their HD movie watching experience (with enough skills to update the ATI driver !) do an update.

**Note: if you are not absolutely sure or never know how to recover from a crashed video driver, do not attempt to do it, it may fail.**

Here is how (I did it sooo many times that I can be sure it works, with my Lenovo T400 and ATI Radeon HD 3400):

1) Download the new driver from this page (11.2, released 2 days ago, 2/15/2011): [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) . Perhaps you better make sure that your card is compatible with the new driver, so you can use this page: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

2) Get rid of the old proprietary driver (if any) using this procedure (NOTE: if you never installed any ATI driver, even from Jockey, you do not need to do the below procedure ! If you do even attempted before, then just do it):
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

> 
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg


After finishing, restart the computer. It will give an error that it can't load fglrx, just choose to use "low graphic mode" just for one session.

3) Install ATI new driver, following the procedure listed for your OS here: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

For Lucid (but mostly also for Maverick) this is the one:

Open the terminal and locate the folder where you place the .run file, then do:

> 
sudo sh ati-driver-installer-11-2-x86.x86_64.run --buildpkg Ubuntu/lucid
sudo dpkg -i fglrx*.deb
sudo aticonfig --initial -f


Restart the computer, and you should be done !

):P

---

### Post by martywd on 2011-03-03
@typhoon_tip:  Good help and instructions!  This worked perfectly for me.

Thank you!

---

### Post by Linux Lurker on 2011-03-10
> **typhoon_tip said:**
> 
**Note: if you are not absolutely sure or never know how to recover from a crashed video driver, do not attempt to do it, it may fail.**

<snip>

3) Install ATI new driver, following the procedure listed for your OS here: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

):P

@typhoon_tip - THANK YOU.

I just got the ASRock E350M1 motherboard combo.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157228](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157228)
I too saw the same "AMD unsupported hardware" logo in the lower right corner of the screen.
Your instructions worked well for me, for the most part. Not sure if, or where I strayed off, but I had to reboot to recovery mode with networking, and continue instructions from building packages again.
Irrespective, it eventually worked for me. Thanks again.

========
I wanted to add some key words, so that when other owners of this soon to be very popular board need video driver help, this post shows up.
ASRock E350M1 zacate AMD hardware unsupported logo driver
ATI Catalyst Proprietary Display Driver Linux x86 x86_64
ati-driver-installer-11-2-x86.x86_64.run
========

BTW... if anyone's interested. This board was a VERY easy build. Going to use it as an HTPC running MythTV. It'll also serve as a general use computer for the bedroom.  So, I installed Kubuntu.  All in all, not enough time to comment on much other. Except, it was a super easy build, and getting everything loaded the way I desire hasn't been difficult either.  I had to change the "Zoom" setting in MythTV Frontend | TV Settings | Playback... to off.  Otherwise, it was giving me a dual, horizontally split screen with duplicate images...
That's all I've got so far. (Sorry to stray off topic).

---

