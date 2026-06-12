---
title: "NVIDIA GeForce 950 Driver"
date: 2015-11-13
forum: Hardware
---

### Post by that_guy2 on 2015-11-13
Hello everyone. I'm fairly new to linux and am having a rough time getting the Nvidia proprietary driver to work. I am using 14.04. I've followed the many guides online with little luck. I recently added the PPA, which shows the list under Additional Drivers. When I try to select driver 352.55, it starts applying then stops half way through and reverts back to the Nouvea driver. I'm not sure what else to try at this point.

At one point I did get it installed (not through the ppa), but then my resolution became locked to 1024x768 with no higher selection (I normally use 1440x900). It's actually still not able to go any higher, even after many reinstalls of Ubuntu and various other distros.

My last effort was this: [http://ubuntuforums.org/showthread.php?t=2263316](http://ubuntuforums.org/showthread.php?t=2263316)
But I don't understand anything after turning the file into an executable.

Any help would be so greatly appreciated, as I'm in school online and this issue makes it very stressful.

---

### Post by howefield on 2015-11-13
Is it possible to try a later release of Ubuntu, 15.10 perhaps ?

I'd normally not suggest moving from an LTS release but I never had much luck with 14.04 and nvidia drivers, albeit with an older card than you have.

---

### Post by tokyobadger on 2015-11-13
Before upgrading the distro (eg 14.04 to 15.10) it would be good to understand your set up in more detail.

1. Which release of 14.04? The latest is 14.04.4

2. Desktop or laptop? Hardware list

3. Which PPA did you add?

4. You got the nvidia driver installed once but not by PPA - how did you install?

5. Monitor resolution - sounds like a laptop; how do you know the max resolution? Do you have xorg.conf in /etc/X11/?

6. Which other distros did you try (with version numbers)?

7. What is the output of ```
sudo apt-get install nvidia-352
```
run that in the terminal

---

### Post by that_guy2 on 2015-11-14
Hey guys, thanks for the replies. I was using 14.04, not sure which release of it. I tried 15.10 from a live usb, but after selecting Try Ubuntu without Installing, I get no signal (black screen).

2. Desktop
3. deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) trusty main
([https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa))
4. I've tried so many I wish I would have taken note which guide worked.
The one that did permanently screwed up resolution (even through live usb's)
5. 1440x900 is what I've always used. It's always been the max selection.
6. Tons of Ubuntu/Debian based distros. Fedora (latest), OpenSuse (latest - Tumbleweed)
7. I haven't been able to get to terminal recently, read below:

Tonight I ended up taking out the GeForce 950 and putting my Radeon R7 250 back in (along with the hard drive I was using at the time, with Linux Mint 17.1 XFCE installed). Tried to boot up and now it gets no signal while booting the through the start screen and bios menu, so I can't access it. I get a signal once it gets to the Linux Mint user login, but with a resolution of 800x600. Once logged in and in display settings, I have the same issue, no selection for a higher resolution. As you can imagine, doing anything at that resolution on a desktop monitor is difficult. I should also mention I've using DVI.

I can't figure out what the deal with the resolution is. How could it now be locked so low like that even with live usbs and also after switching back to my old graphics card? Can something like that getting stored in UEFI? I've only had this motherboard (Gigabyte F2A68HM-H) a few months and its my first with UEFI.

I'll run sudo apt-get install nvidia-352 and let you know the output once I can get back in terminal (if I can).

---

### Post by tokyobadger on 2015-11-14
Thanks for the answers. The ppa is the same one I'm using with my GTX680 on 15.10 and 16.04 (but also used on 14.04, 14.10, 15.04, elementaryOS, and Mint17.2) however I always install from the terminal and I'm using currently nvidia-358. 

The last drivers that gave me grief were the 331.xx and 334.xx series that were in the standard repositories. At that time I started using the xorg-edgers ppa and then when Ubuntu set up the semi-official graphics-drivers ppa I switched over.

The issues I faced with the 33x series were the infamous flickering/rendering problem and then the persistenced problem, both resolved with the 34x series (as I recall). However, automatic setting of maximum resolution was never a problem.

The issue of no signal while booting to the BIOS (actually in your case booting to UEFI which replaced BIOS) is not an nvidia issue nor a linux issue as UEFI uses Graphics Output Protocol (GOP). My questions to you would be: 

1) before the new motherboard did the Nvidia and/or Radeon cards give you the correct resolution?
2) since installing the new motherboard have you ever achieved the correct resolution with the Nvidia and/or Radeon cards?
3) do you have windows on this desktop and if so does it give you the correct resolution with the gfx cards?

I'm starting to suspect that your issue is one of the following (in no particular order):

1) monitor
2) DVI cable
3) PCIe slot on the motherboard (did you try different ones?)
4) graphics card
5) UEFI setting
6) motherboard itself

---

### Post by that_guy2 on 2015-11-18
Sorry it's taken me so long to reply. I had to take some time off from this issue, as I'm 2 weeks behind on school due to this.

1. Yes
2. Yes
3. No. I do have a mini PC with Windows on it that my dad let me borrow for my online classes.
No issues with the resolution on that, using the same monitor and DVI cable.

My 1st guess is something to do with the UEFI settings like you mentioned. 

I recently found this: [http://ubuntuforums.org/showthread.php?t=2302820](http://ubuntuforums.org/showthread.php?t=2302820)

Someone mentions I may need the latest kernal. Anyone know if this is the case?

---

### Post by tokyobadger on 2015-11-18
If #2 is yes can you describe what you did at that time?

I'm more inclined to think it is the PCIe slot (did you try another?) or the motherboard if #2 were positive previously

---

### Post by oldfred on 2015-11-19
The newer Maxwell nVidia cards seem to need newer kernels & drivers.
Did you install nVidia driver more than once? Or from different source(s)? If so you must totally purge all nVidia before installing another. Somehow they conflict and create issues, you just cannot install a different driver from a different source.

 The Extreme Cases Where A NVIDIA GTX 950 Can Outperform An AMD R9 Fury On Linux OpenGL
[http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-fury&num=1](http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-fury&num=1)
NVIDIA's GeForce GTX 950 Is A $150+ Bargain For Linux Gamers
[http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nv-gtx950-linux&num=1)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)

---

### Post by that_guy2 on 2015-11-26
Sorry I'm just now replying again. I mostly likely won't try to get it to work again until classes are over on Dec 4th.

@tokyobadger
It's a mATX, so only 1 PCI-e. :(

@oldfred
Thanks for the reply. I'll be sure to check out those links after this semesters over. :)

---

### Post by tokyobadger on 2015-11-28
oldfred is right, you need to clean out all previous nvidia driver installs

re: the UEFI settings have you updated firmware/changed settings since the last successful achievement of correct resolution with the nvidia card?

---

### Post by that_guy2 on 2015-12-18
This semester's out and I'm back to trying to get this to work. I'm not really sure where I left off, but I can't even boot a live usb. I select try Ubuntu without installing and then the monitor loses signal (black screen).

---

### Post by that_guy2 on 2015-12-18
Screen goes black after selecting Try Ubuntu without Installing in both UEFI and Legacy.
I have a fairly new NVIDIA GeForce GTX 950.

---

### Post by sudodus on 2015-12-18
1. Try with the boot option **nomodeset** (and maybe also some other boot options).

See this link: [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

2. Try with the newest Ubuntu version, **15.10**,

3. or even the next version (now during development) Xenial Xerus, to become 16.04 LTS. You can find it via the testing tracker

[Testing tracker download links for Ubuntu Desktop amd64](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/108863/downloads)

---

### Post by that_guy2 on 2015-12-18
Thanks for your reply sudodus. I've tried both 15.10 and 16.04 daily build.
I clicked the link but I more the less just got confused.
How do I select / add the nomodeset boot option?
Sorry I'm still learning linux!

---

### Post by sudodus on 2015-12-18
In the link [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) there is one description for UEFI mode and one description for BIOS mode. So you browse to one of those links and follow that description.

If you still have problems, please tell us which mode you are running (UEFI or BIOS), and you can get more details.

---

### Post by that_guy2 on 2015-12-18
Thank you, I think I understand it now. 8-[
I found a live usb  with BackBox on it, tried that, and oddly enough it booted just fine (think it's based on 14.04).
But now I'm  back to original problem of having a locked resolution. I'll install it and try to install the new NVIDIA drivers. [-o<

---

### Post by oldfred on 2015-12-18
If running the newer Ubuntu versions, you can install from system settings.  If not or you really want the very newest nVidia driver version add a ppa where a trusted source creates the install files for Ubuntu. Ubuntu now has a ppa for video and expects to add it to the install in the future as an option. Do not install directly from nVidia as .run file. While that works you have to redo the install after every new kernel.

       Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

   # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices
sudo apt-get update && sudo apt-get install nvidia-3xx
# I usually use nvidia-3xx-updates, where 3xx is newest available, if older card do not install newest version, check correct legacy version from nVidia.
# While you're at it upgrade libvdpau & nvidia-settings

---

