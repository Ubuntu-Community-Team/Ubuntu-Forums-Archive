---
title: "ubuntu 9.10 and emachine netbook em250"
date: 2010-03-04
forum: Hardware
---

### Post by thatscold2 on 2010-03-04
Greetings , this will be my first post to the forums so if I do something outta line I'll apologize right now :) .
Bought a wallyworld emachines em250 netbook , wanted something small light n cheap to tote around seemed like a good mix. Came with xp , but Ive been playing the 9.10 on some other equipment figured Id load that , dual boot. I setup the bootable thumbdrive , loaded the ubuntu netbook version , on the live thumbdrive load prior to the dual boot setup it coughed up that I would need a non free driver for the wifi , no big deal I thought so I went thru with the actual load and setup . When I restarted it everything else seems functional but the wifi , and now for some reason I don't have the non free driver download , for all intents I dont think it even sees the built in wifi anymore . I thought I would try loading the desktop version of ubuntu to see if that worked ( I would actually prefer that anyways) but the same thing with the wifi . So now I have a bit of an issue I have xp , ubuntu netbook , and 9.10 desktop installed on different partitions  , Id like to keep the xp just for some compatibility program issues but Id also like to nuke one of the ubuntu versions , not sure how to do that , was looking at windows partition manager programs but little tuff since no cd rom for install 

So long story short , hoping that someone can help with the driver issue for the wifi on the netbook and then also give me an idea of how to eliminate whichever ubuntu version I don't need or if I can't get either working both so that can try other distros and see if I can find one that plays nice with the wifi .
Sorry for the length of all that 

thanks in advance 

cheers
thatscold2

---

### Post by luinnar on 2010-03-16
Your are lucky one because I solved the same problem yesterday on the same netbook! I spent the whole yesterday evening and this morning to fix the issue. I tried many things, but in fact it's necessary to do only few steps:

1. Download Broadcom 802.11 Linux STA driver from the following web page:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

2. Extract and build the driver. Below is a description of this step from README.txt:
[quote=README.txt]
BUILD INSTRUCTIONS
------------------
1. Setup the directory by untarring the proper tarball:

For 32 bit:     hybrid-portsrc.tar.gz
For 64 bit:     hybrid-portsrc-x86_64.tar.gz

# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz

2. Build the driver as a Linux loadable kernel module (LKM):

# make clean   (optional)
# make

When the build completes, it will produce a wl.ko file in the top level
directory.

If your driver does not build, check to make sure you have installed the
kernel package described in the requirements above.
[/quote]
Got from here: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

3.  Now you need to run 'sudo make install' from the same floder where you ran 'make'.
The driver wl.ko will be installed into the following folder:
/lib/modules/<kernel-version>/kernel/net/wireless

4. Now you need to load this driver into the system.
You can do this by performing the following commands:
# cd /lib/modules/<kernel-version>/kernel/net/wireless
# sudo depmod
# sudo modprobe wl
Please note that <kernel-version> is a string with YOUR linux kernel version,
so you need to adjust the first command.


When I have done all this, Wi-Fi on my Emachine em250 got working!:D
I hope this will help you and anyone who faced the same issue.

---

### Post by ponderota on 2010-11-02
Hey, how did you find your emachines went with the bluetooth?

I just bought an EM350 and found that the bluetooth isn't recognised in Ubuntu. I'm thinking at this stage that it may be the old "disabled in Windows, unable to be enabled through Ubuntu" trick.

---

