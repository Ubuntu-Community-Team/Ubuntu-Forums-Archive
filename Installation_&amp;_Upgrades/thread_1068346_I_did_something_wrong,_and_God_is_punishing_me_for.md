---
title: "I did something wrong, and God is punishing me for it."
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Aped on 2009-02-12
[Sorry in advance for the long-winded story, and for spelling 'disc' as 'disk' because 'disc' looks weird to me.]

So! As with many people these days, I have become fairly disinterested in Windows in general and finally decided to go full Linux. I've used it a bit before, am not a complete moron, but still seem to be failing in a few basic areas. Like, the installation. 

My first mistake was probably getting ambitious and installing the 64 bit version instead of the 32. No matter, though; issues should be about the same. 

So I booted into windows, used the CD's option to force a boot from the disk (it didn't want to load normally) and was on my way to having a functional install. Everything went fairly smoothly, ubuntu 8.10 was on my machine! Except my wireless network wasn't working. Fine, whatever, I installed an old copy of fedora on top of ubuntu (Fedora 8, had the disk sitting around somewhere) and it *could* connect to my network, although just momentarily. Crap. 

Here's where it gets fun: I got a new wireless card to use instead of my onboard (Asus P5K-E WiFi-AP Mobo) one, in case the specific nature of my adapter was foiling the prepackaged drivers. Fedora doesn't recognize the PCI card properly, now I have no networks; neither the G nor the N which my router broadcasts. 

Additionally, I can no longer install other operating systems on my computer! Ubuntu 32 AND 64 disks just fail and Fedora boots up instead. In my desperation, I reached for the XP CD; if I reinstalled that, and *then* did ubuntu again (making sure to find some drivers for my various network adapters in the meantime, in case the much-newer ubuntu also failed to recognize this new card - D-Link DWA-552 Xtreme) perhaps all would be right with the world. 

And yet, no, the XP boot disk is recognized - unlike ubuntu 64 or 32 - but hangs after trying to get my comp's hardware information. 

So, I have two issues here, not related per se but at least intertwined. Did the option I chose when I first installed ubuntu, to modify the boot record thingo, screw with my ability to boot from other sources? Is there a way, from Fedora 8, to start an install of Ubuntu from the disk?

Did I fail as early as the disk-burning process? Is there some toggle not provided by windows' integrated CD burner to make a disk bootable? 

What the hell is wrong with my wireless adapters, are they not *good* enough for you, ubuntu? 

Any help would be appreciated; if you have questions about my configuration or things I did during install, I would be MORE than glad to get that info for you.

Render unto me your secrets, you knowledgeable elite!

---

### Post by k3rnelmustard on 2009-02-12
I just have a couple of questions.  Why were you trying to install ubuntu from windows, you said you couldn't boot from the cd?  But you must have set cd as a preferred device to hard drive since the xp bootable cd works?  What do you mean the ubuntu 32 and 64 disks just fail?  What does it say?

---

### Post by Aped on 2009-02-12
> **k3rnelmustard said:**
> I just have a couple of questions.  Why were you trying to install ubuntu from windows, you said you couldn't boot from the cd?  But you must have set cd as a preferred device to hard drive since the xp bootable cd works?  What do you mean the ubuntu 32 and 64 disks just fail?  What does it say?

I initially put the disk in when windows was running, then selected 'reboot', pressed F8 like a madman and told it to boot from the CD drive, which it didn't do. I then, having been booted back into windows, pressed the bottom-most option, to change boot something something and restart (said it was seldom required) which worked. 

I did set CD as preferred in my BIOS settings; it is still that way now. 

The ubuntu disks no longer are recognized as bootable, I assume; when I have them in the tray, the loader defaults to Fedora 8 and does not have ubuntu as an option; ubuntu does not load, there is no message one way or another. 

Will a sudo rm -rf / work?   :(

---

### Post by k3rnelmustard on 2009-02-12
I think something's wrong with your BIOS checking the boot cd.  Since the xp disk was recognized, it's possible that the windows bootloader decided to boot it rather than your BIOS.  I believe that if a windows cd is in the drive the windows bootloader will give you the option to boot from it, but I'm not totally sure.  Either you're pushing the wrong button to boot from cd or ur ubuntu cd is messed up.  Maybe you should try a different one / try using F12 or F10 or something instead of F8.


[quote="Aped"]
Will a sudo rm -rf / work?
[/quote]

Probably not, but what are you trying to do with it?

---

### Post by Aped on 2009-02-12
> **k3rnelmustard said:**
> Either you're pushing the wrong button to boot from cd or ur ubuntu cd is messed up.  Maybe you should try a different one / try using F12 or F10 or something instead of F8.


Ubuntu disk is the one I successfully installed from to begin with. Now all I get is Fedora's GRUB with no option for Ubuntu.

I want to format the drive so that I can start from scratch again, of course.

---

### Post by k3rnelmustard on 2009-02-12
No, I don't think rm -rf / will work for that!  I think there's something wrong with the way you're trying to boot the cd... if not there's something wrong with the cd.  Sorry I can't be more help, but if you can get the cd to boot it should be a pretty simple process.

---

### Post by Aped on 2009-02-12
> **k3rnelmustard said:**
> if you can get the cd to boot it should be a pretty simple process.

Tell me about it. I'll re-burn the image I guess and have another crack at it.

---

### Post by vrms9 on 2009-02-12
Hello,

I have installed wine and ie6 in ubuntu 8.10. When I tried to run ie6 from terminal I am getting the following error message. pl help me to solve this problem


root@venkatesh-desktop:~# ie6
xhost:  unable to open display ""
sudo: no passwd entry for wine!

venkat
india

---

### Post by Aped on 2009-02-12
Are you attempting to HIJACK my whining thread with your whining? Go make your own beg-thread!

---

### Post by estyles on 2009-02-12
It really seems like your BIOS does NOT want to boot from the CD.  Fedora should have nothing to do with it, and really even a messed up CD should still *try* to boot up.  In your BIOS settings, try setting the first boot device to CD and then either turn off the other boot devices or set them to like floppy and network or something.  Don't give it the option to boot from hard drive, and see what it does...  You can always change those options back the next time you reboot.

It really doesn't appear to be cooperating at all...

---

### Post by Aped on 2009-02-14
estyles, s'exactly what I ended up doing and it worked. Really finnicky BIOS I guess (I also re-burned every CD in question, which may also have solved it).

Thanks to all who posted in this thread. Now all I need to do is [get my wireless adapter up and going](http://ubuntuforums.org/showthread.php?t=1069947) :D Many <3s and happy v-day

---

