---
title: "NVidia 8800 GTS, worth my trouble?"
date: 2010-09-01
forum: Hardware
---

### Post by ladasky on 2010-09-01
Hi folks,
 
I was recently given an NVidia 8800 GTS video card as a gift!  It would be great if I could add this card to my Ubuntu system.
 
I use the molecular dynamics simulation _[GROMACS]("http://gromacs.org")_, and there is now _[a version which takes advantage of CUDA]("http://www.gromacs.org/Downloads/Installation_Instructions/Gromacs_on_GPUs")_.  I also use _[PyMol]("http://pymol.org/")_, which has known issues with ATI graphics accelerators, but is reported to play nicely with NVidia.
 
Unfortunately, my attempts to add this card to my system have failed. I see that this card has shown up on the _[desktop hardware incompatibility list]("http://ubuntuforums.org/showthread.php?t=361237")_ several times, but I don't see it on the _[compatibility list]("http://ubuntuforums.org/showthread.php?t=361236")_.  Should I bother at all?
 
If you are still reading this, then you think there's a chance I might not be wasting my time.  So let me tell you about my system, and my installation attempt.

My current OS: Ubuntu 9.10 Karmic

Motherboard: Gigabyte GA-MA78GM-US2H, has a built-in ATI Radeon 3200 GPU (which does very little for me, I have to run it with compiz turned off if I want to use PyMol).

CPU: AMD Phenom X3 720, 2.8GHz.
 
The hardware part of the installation went nominally well. I attached the DVI video cable to the NVidia card, and got the BIOS splash page on boot-up.  After an unusual long pause, I received an error message: "(EE) No devices detected."  This was apparently not a fatal error, the system informed me that I would just have to run Ubuntu in low-resolution mode until I fixed it.
 
There were four options to follow at this point.  They involved examining and saving a log file, troubleshooting, restoring old settings, or just running in low-res mode for that one session.  Whatever I chose, I eventually got to the point where I should expect a login prompt to appear.  At this point the screen went BLACK and the system just hung.
 
Removing the NVidia card from my system, fortunately, allowed my system to boot normally.

Now, I know that I don't have any NVidia drivers installed at this point.  I've never installed a video driver on Ubuntu before, except when I install the OS itself.  Correct my thinking if this is wrong, but it seems to me that installing the NVidia driver before I've even installed the card would be putting the cart before the horse.  It might even conflict with my ATI driver?  I'm thinking that I should boot into low-res mode, allow Ubuntu to identify the GPU just as it did when I first installed the OS, and then ask me if I want to install any proprietary drivers.
 
I will consider upgrading the OS to 10.04 if it will help.
 
Thanks for any advice!

---

### Post by Fafler on 2010-09-01
It should be pretty straight forward. Press ctrl+alt+f1 and you should hopefully get a text login prompt. Login and type

sudo dhclient
sudo apt-get install nvidia-current

Now reboot and hopefully everything should be okay. If you can't get to the console, you need to boot into textmode instead. Get back if you need to. Anyway, the 8800 GTS should work flawless.

---

### Post by ladasky on 2010-09-01
Hi, Fafler,
 
Thanks for the quick reply.
 
Ctrl-Alt-F1 takes me to a black screen when I have the NVidia card installed.
 
But when I have the card removed and I boot into normal graphics mode, Ctrl-Alt-F1 will take me to the text login prompt that you hoped I would see.  Unfortunately, I'm using the motherboard's built-in ATI video at that point.
 
Additionally, I looked through the list of available packages in Synaptic. There is no "nvidia-current".  Do I need to add a specific repository to make a package with that name visible?  Is it a meta-package?  There are many packages with names like "nvidia-glx-173-dev" and "nvidia-185-kernel-source."

---

### Post by ellgor on 2010-09-01
Hi,

If your still having problems I found this guide that works:


1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

### Post by ladasky on 2010-09-01
Hi, Ellgor,
 
Thanks for the detailed information.  Where did you find it?
 
Also, when should I install the NVidia card? Between steps 4 and 5 I presume?

---

### Post by paulisdead on 2010-09-01
Just thought I'd chime in and say not all the 8000 series nvidia cards are cuda capable.  I believe there were 3 that couldn't do it, the 8800GTS 320MB, the 8800GTS 640MB, and the original 8800GTX (I think it had 768MB).  I've got the 640MB model, so no VDPAU or cuda for me.  There was a 512MB 8800GTS that has cuda and VDPAU.  So check if the model you have supports it, before you tear your hair out trying to get cuda working.

---

### Post by ladasky on 2010-09-01
Hello Mr. McCartney.  ):P
 
The video card is actually an OEM card.  It's the NX8800GTS-T2D640E-HD-OC from MSI.  It's an NVidia GeForce 8800 GTS under the hood.  MSI's _[features page for the card]("http://www.msi.com/index.php?func=proddesc&maincat_no=130&cat2_no=&cat3_no=&prod_no=1153")_ says that it is CUDA-capable.

---

### Post by ladasky on 2010-09-02
> **ellgor said:**
> Hi,

If your still having problems I found this guide that works:

_Update:_

I tried to follow ellgor's nicely-detailed guide, and unfortunately it doesn't work for me.  I'm basically stuck at the exact same point as before.  Here are my notes:

Steps 1-4 went smoothly.
 
I inquired about when to install the video card in an earlier post.  Since I didn't get an answer, I took my best guess and modified step 5.  I shut the computer down, installed the graphics card, attached the video cable, and rebooted.
 
At step 6, I did not receive an error message saying that NVidia drivers could not be loaded.  Instead, I received the same error message I had before, "no devices detected."  As before, trying to exit to a text-prompt login gave me a black screen.  Pressing Ctrl-Alt-F1 did not remedy this.
 
Fortunately, uninstalling the video card and switching back to the on-board ATI video went smoothly.  I was worried that on-board video might be affected by my editing of the blacklist.conf file.  It was not.  Regardless, I will comment out the lines I added to blacklist.conf for now.

At this point, I'm wondering whether a subtle difference between the fact that this card is actually from MSI rather than NVidia is responsible for the failure to install.  MSI's web site does not offer Linux drivers, it only supports Windows... :icon_frown:  ...but _[a discussion I found on the MSI forum]("http://forum-en.msi.com/index.php?topic=116824.msg879850#msg879850")_ suggests that MSI (quite sensibly) does not alter the NVidia drivers, they just bundle them with an overclocking utility (which I expect I don't need or want).

---

### Post by paulisdead on 2010-09-02
Try putting the card in, and when you bootup, go into recovery mode.  I believe you had to hit ESC on the grub prompt to get the menu list, if you don't multiboot with other OSes.

Once you're up and running in recovery mode, I think it prompted you if you wanted to start the network, which you'll want to do, but not do a full boot.  If it doesn't start the network, or give you the option, you should just be able to run "dhclient eth0" (If eth0 is normally your nic, substitute the right device if you use something other than eth0).  Then run "apt-get install nvidia-current" and hopefully that should take care of you when you reboot again.  Either that, or you can install the drivers from nvidia's site as recommended, instead of using the ubuntu nvidia-current package.  If the kernel gets upgraded you'll have to do this again, if you use the ones from their site.

You might also try disabling the onboard video in the bios, when you put the nvidia card in, if you haven't tried that.

You might also want to look at the Xorg files in /var/log.  You may need to look at a few of them to determine which was the one when you tried to start up with the nvidia card in, and which was with the onboard.

Also, it being MSI doesn't matter.  Nvidia doesn't actually make graphics cards, they just make graphics card chipsets, and it's up to an OEM like MSI, Asus, EVGA, etc to make an actual product out of it.  There are a handful where something's been tweaked, and they don't conform to what the drivers expect, maybe a differing PCI ID or something, but most should be compatible with the drivers from nvidia.  All of us using nvidia cards have them from a 3rd party manufacturer, but most are using nvidia's drivers to run them.

---

### Post by lidex on 2010-09-03
I would uninstall ati drivers and remove xorg.conf then shutdown. Change cable to the 8800 and boot up to the bios screen, enter bios setup and disable onboard graphics. Xorg may complain and at that point boot into low graphics mode. Once at the desktop run hardware drivers (jockey) and install recommended drivers. Reboot.
Now go to a terminal and run this command:
```
sudo nvidia-xconfig
```
Reboot again.

---

### Post by Fafler on 2010-09-03
One thing that would work for sure: reinstall with the Nvidia card in the machine.

Does anyone know where Ubuntu keeps info about which driver it want to use for Xorg when it doesn't use xorg.conf? It knows to load the ATI driver (which doesn't work) instead of autoprobing, where what tells it to do so? Ubuntu keeps getting more and more like Windows, and that's sometimes a good thing, but mostly it's just annoying.

---

### Post by hsoulen on 2010-09-03
Just a quick "chime-in"...

I think the advice earlier in this thread to remove the ATI drivers may be looking in the right direction, I would also check in your BIOS and see if there is an option for disabling the on-board video, could say something under "On-board devices" like "Use on-board VGA or Use PCI device" or some such option.

Thought would be to try the following:

[LIST=1]
[*]With the NVidia card installed, go into the BIOS and see if you can disable the on-board video
[*]Boot the live CD and check the discovered hardware devices
[/LIST]
My two cents, worth one cent.

Hank

---

### Post by ladasky on 2010-09-09
Hi, everyone...
 
I really appreciate the continued advice and insight.  I'm trying to implement your suggestions, but I'm taking an unexpected, grand detour.
 
First, I wanted to check my BIOS as recommended by hsoulen.  Well, I had a bizarre problem.  I couldn't enter BIOS!  My keyboard was not registering at boot time, even though it worked fine once I got to GRUB.  If you're really curious about this tangential problem, you can send me a private message.
 
Anyway, I fixed the keyboard problem.  There was only one setting in the BIOS which pertained to video.  The setting determined whether the on-board video or the PCI peripheral slot video would be tried first.  This was already set to PCI, which is what I will need.
 
I still get the black-screen problem when I try to follow ellgor's protocol, though.
 
So I think that fafler's suggestion of re-installing the OS is the best way to proceed, even though that seems like such a Windows thing to do.  ;)  That is what I'll try, after I've backed up my home folder.  Alas, my home folder has recently grown quite a bit.  And I've discovered that Brasero quickly becomes obnoxious to use once the amount of data you want to write exceeds the space on one DVD... :mad:
 
I'm now looking for a backup utility which will do a nice job of archiving about 15 GB, without me having to wrestle with it.  I have a second Linux machine in the house, I might do a network backup.  8-) 
 
Once my data is safe, I'll proceed.  Thanks again!

---

### Post by ladasky on 2010-09-10
Thank you everyone!
 
Reinstalling the OS worked.  I have the NVidia card running with Ubuntu 9.10, and I don't have to turn off compiz to get PyMol working.  :D  On to CUDA I go!
 
I would have enjoyed taking a shortcut, but at least I achieved the result I wanted.
 
It would be VERY nice if the Linux gods would give us a single directory for application software.  When I tried to do a partial-reinstall of the OS, without re-formatting my root directory mount point, it failed.  I had to re-format.  I had set up a separate /home mount point which was undisturbed, and that's good.  But I've spent quite a lot of time putting my various applications back in place.

---

