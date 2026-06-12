---
title: "First install, boots into X, brown background with junk in the middle..."
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by orangedoor on 2006-01-31
I installed ubuntu (single cd installation). Everything went fine, I did a couple debian installations on this computer last week, so install was the same.

Problem is after installation I boot, and it goes into X-windows but there is a brown background/wallpaper (after logging in), and in the middle is a rectangular box of screwed up colors and static. I can't interact with the desktop in any way.

I had successfully configured X to run previously with Debian after some finagling. The issue is that I have an nVidia 7800gt and the Debian install I had to use the vesa drivers, and then install the nvidia drivers later. I probably just need to run the configurator for X, or edit the config file manually, but I'm not sure what I should change that's probalby wrong right now. Also I'm a real noob with running linux on the desktop (and pretty much a noob in shell too, but I can edit files with vi and get around the file system).

Thanks for any help or pointers in the right direction. I had tried some forum searches but found my issue difficult to describe and therefore didn't find any helpful threads.

---

### Post by orangedoor on 2006-01-31
Follow up:

I rebooted the computer and continued with the normal boot (not recovery). At the login screen, I clicked on "Session" and decided to try Gnome. After I clicked it the window with the list of different possible "Sessions" got garbled up graphically and froze the computer or screen or w/e I should call it :)

---

### Post by orangedoor on 2006-01-31
I rebooted again, this time in recovery mode. After some searching I found that X config file (xorg.conf i think) and see that it's setup to use the "nv" driver, as well as loading most of the modules (previously in Debian I read that I needed to disable some for it to work).

I was hoping that with this installation it would just work and come with the nvidia drivers because I had issues trying to download and install them previously. So I'm reluctant to change to vesa, and then try to install new nvidia drivers... although that is probalby what I have to do... bah! I guess it'll be a learning experience.

I'll wait till somebody responds on here before doing anything I will have trouble reversing.

---

### Post by orangedoor on 2006-01-31
I edited the xorg.conf file and just changed driver "nv" to "vesa." X is working fine now. So it's definetely that, although if there's a way to have the included nvidia driver work by changing something else in the .conf file that'd be great. I don't want to do too much in vesa mode only to screw it up trying to install nvidia drivers later, and I think I do need nvidia drivers installed to properly run wine (that should be fun to setup) and play video and do other graphics card instensive stuff.

---

### Post by orangedoor on 2006-01-31
Well I'm not the most patient guy and like trying to figure things out myself, so I ended up finding the wiki entry for installing the binary drivers. ([https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)) . 

The process appeared very simple, so I gave it shot.

After I ran the command "sudo nvidia-glx-config enable" I got an md5 checksum error, it gave me an option to I think basically override it, or by changing the driver in the xorg.conf from "nv" to "nvidia" . Mine was currently "vesa" and I tried changing in the terminal but it wouldn't let me because it was write protected.

I rebooted into the recovery mode (although I'm sure there's a simple way of shutting down X) and edited the file to "nv" and ran the sudo command again. It didn't give me an error, and the "nv" was changed to "nvidia" in the file (I guess I could have just done that). I ran "startx" and the background looked different (B&W grid with dots) and it didn't show the nvidia logo. I tried ctrl-alt-backspace to restart X but that just seemed to shut down X and not restart it. So I restarted the computer, and it goes into the regular pretty X again, and seems to be fine just like it was in "vesa" but the nvidia logo doesn't show up.

How do I check to see if my nvidia drivers are setup and running properly?

I'm pretty sure they are running, but want to make sure. For my test I tried opening up one of my movies from an ntfs partition, and this time instead of giving an error, it opens up in Totem and just says decoders not fine, which is a good sign to me since I'm sure I lack the codecs to play the xvid and divx files.

---

### Post by MartinG on 2006-01-31
The major reference for installing the proprietary nvidia drivers is tseliot's howto:
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

If you run "lsmod | grep nvidia" this will show whether the nvidia driver is loaded (if it's not, run lsmod without an argument and search it).  The nvidia splash screen only shows up very briefly when X is launched, sometimes (on my system) not at all; blink and you've missed it.

If you follow the howto above you will install the nvidia-settings GUI, or you may wish to install nvidia-settings from synaptic.  This will show if you have the right driver, and may help you configure it better.

---

### Post by Haegin on 2006-01-31
Is this occuring after you login or before? It may be the gnome splash screen giving you problems...

---

### Post by orangedoor on 2006-01-31
Thank you Martin, that is very useful info. (Particularly getting the GUI set up)

Human: upon original install the garbled screen was where it says Ubuntu in the middle and then the icons for the things that are loading.

---

