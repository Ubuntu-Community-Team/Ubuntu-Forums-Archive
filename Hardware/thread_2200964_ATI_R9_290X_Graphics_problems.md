---
title: "ATI R9 290X Graphics problems"
date: 2014-01-22
forum: Hardware
---

### Post by neph01 on 2014-01-22
Is this thread still actively maintained? I've been trying to figure out what the hell is wrong with my system and I think this issue might be related. I have a desktop with a newly installed R9 290X, but the motherboard's integrated graphics is intel of some kind.

I had originally tried to follow the instructions laid out here: [http://askubuntu.com/questions/392337/system-hangs-installing-13-10-with-amd-r9-290x-graphics-card](http://askubuntu.com/questions/392337/system-hangs-installing-13-10-with-amd-r9-290x-graphics-card)
(and therefore here: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD#Manually_installing_Catalyst_13.4](https://help.ubuntu.com/community/BinaryDriverHowto/AMD#Manually_installing_Catalyst_13.4))
since I thought this described my issue very well, but after installing Catalyst, restarting would freeze up on boot splash as before. As a result, I've been frantically trying to find the problem. I think it is that my motherboard's integrated graphics and my GPU are not of the same architecture, and so I *think* this thread is relative to my problem.

The trouble is, when I try to follow the instructions at the beginning of this thread, I get stuck at the step where I am to reboot my machine after installing fglrx - I, again, get freezing on the boot splash every time and have to do a fresh install.

I have no idea how to proceed or what I should do. I have outlined my problem in detail here: [http://askubuntu.com/questions/408455/installing-proprietary-drivers-for-r9-290x-gpu-on-ubuntu-gnome](http://askubuntu.com/questions/408455/installing-proprietary-drivers-for-r9-290x-gpu-on-ubuntu-gnome)
But no one has answered.

Any input would be appreciated. I am very much at a loss. If this is not the right thread, because my issue does not appear to be related to hybrid graphics, please point me in the right direction.

---

### Post by QIII on 2014-01-22
Moved to its own thread.

Hello!

Hybrid graphics are used in laptop systems, so you are correct that the previous thread was not the right place.  It is not likely that any of the instructions you followed are applicable.

Could you tell us what version of Ubuntu you are using?  What Intel CPU?  Most desktop motherboards allow for a choice between integrated and dedicated graphics.  Have you selected dedicated graphics in your BIOS/EFI?

---

### Post by neph01 on 2014-01-22
Thank you for letting me know I was in the wrong place. [Here is my full parts list.]("http://pcpartpicker.com/user/collision115/saved/")

OS: Ubuntu-Gnome 13.10 64-bit ([downloaded from here]("https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME#PC_64_bit"))

My BIOS has an option to set which graphics is loaded first, but I assumed that meant it would still load everything available. I had to select integrated graphics to do the installation. Should I have switched it after installing fglrx? After installing I didn't even necessarily want to use it right away, I was just going to verify that the installation succeeded but I can't.

Oh, one last thing - I was able to boot into recovery mode. Booting from there into failsafe graphics mode doesn't work, it crashes just the same. However, I was able to access a root shell. Running fglrxinfo yielded something along the lines of "display not found" instead of the expected output. If you want me to find the exact wording of that error I can probably get back to it.

---

### Post by neph01 on 2014-01-23
This thread hasn't really gotten much attention. Could someone suggest where else I should bring my problem to get help quickly? I'm still stuck and rather frustrated with this. Any help would be appreciated.

---

### Post by mystyc1 on 2014-01-24
Are you trying to run a single-monitor system or a dual-monitor one?  In either case, consider going into BIOS/EFI and disabling one of the cards/GPUs, if that option is available.  Also, in a dual-monitor system with multiple video devices, Ubuntu can sometimes get confused as to which monitor goes to which device.  If you are able to use only one GPU then try uninstalling the proprietary drivers and allow Ubuntu to install the open source drivers, most of which have more support and a complete compatibility list.  Otherwise, if you want a system that uses both GPUs (or don't have a choice not to), then as QIII said, you are trying to setup a hybrid graphics system.  Check out the documentation availible for "[Hybrid Graphics](https://help.ubuntu.com/community/HybridGraphics)" and see if that helps.  

Also, before you follow any instructions regarding the installation of video drivers, be sure to uninstall any drivers already present if they are not working properly, or were not completely installed. [**[COLOR=#C61919][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170")

---

