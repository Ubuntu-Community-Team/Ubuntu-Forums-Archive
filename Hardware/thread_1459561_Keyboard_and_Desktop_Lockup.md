---
title: "Keyboard and Desktop Lockup"
date: 2010-04-21
forum: Hardware
---

### Post by sself on 2010-04-21
Hello,

I am having an issue with the responsiveness of my keyboard, as well as with the desktop when running Ubuntu. The laptop is an Acer Aspire 6930. When this issue occurs, I am unable to get a response from any key on the keyboard. The mouse cursor will move around and highlight icons on the desktop, including the navigation links to system, places, etc. When clicking on any of the icons, there is no action in response. I have read over the forums for weeks looking for a solution to this problem, and have tried many, many things. Some of the things I have tried include trying multiple versions of keyboard drivers, changing the file system from ext4 to ext3 and doing a clean install. I have used Ubuntu 9.04 x64, 9.10 x64 and 32-bit, 10.04 beta 1 and beta 2. I have also tried the latest Mint distribution, as well as Fedora 12 with gnome. I dual boot Windows 7 on this laptop, but have wiped my drive and installed Ubuntu only, using a few different distributions, all of which demonstrate the same behavior. I'm pretty sure at this point that it is a hardware issue. The only thing out of the ordinary that occurs during these lockups is on the "touch keys" located at the top of the keyboard. There are multimedia keys, volume, play/pause, stop, and track skip. There are also touch keys for toggling the wifi, bluetooth, and launching a web browser. The wifi connection light will blink intermittently, then stay solid for an inconsistent time while this issue is occurring. When I boot into the windows partition the wifi connection stays solid. I do not lose internet connectivity during these times while using Ubuntu, as far as I can tell. I prefer to use Ubuntu, and am required to run a Linux/Unix distribution at my work. This locking up is causing me serious issues. I have exhausted the options I have found in these forums, and others I have searched. Thank you in advance for considering this issue, and any advice or recommendations you can think of. I'll try anything at this point.

---

### Post by dabl on 2010-04-21
I don't have experience on the Acer Aspire, but some newer laptops and netbooks are using very aggressive power-saving techniques, and one that I am aware of (Toshiba NB205) has the hard drive "falling asleep" every so often, if it doesn't get a poke from the (Windows-only) driver.  So when running Linux, certain activities (like running updates in CLI) will suddenly seem to "freeze" until you touch the keyboard or touchpad.

If it is not that, then it is probably a running process sucking up the resources for a period of time.  To find out which process, open a terminal window and run ```
top
```

With top running, move the window somewhere on the screen where you can keep an eye on it.  When the "freeze" happens, take note of the top process -- what is the name of it and how much of the CPU is it using?  That might reveal the culprit.

---

### Post by sself on 2010-04-22
Thanks for the reply. I'll keep a terminal with top open until it happens again. I don't know why I didn't think of doing that in the first place, it's usually one of the first things I do when I'm having any issue. I'll let you know what comes up. Thanks again.

---

### Post by sself on 2010-04-22
ok, it froze up on me again within 5 minutes of booting up. The top of top was Xorg, but was only using about 13% CPU. It started by intermittently not registering input from the keyboard, and within 30 seconds of that, I could no longer type in any window, or move any window with the mouse. I can switch between desktop views and double click windows to resize them, but that is the only interaction with any part of the desktop that I can get. Had to hard reset and boot up windows to respond again. Any ideas?

---

### Post by dabl on 2010-04-22
That's an odd problem.  If it runs Windows with no unusual behavior, then it begins to look like a bug in the kernel to me, or possibly something like udev.  If it's just in the Ubuntu kernel, then one would think you could get a different distribution like sidux or fc to run on it.  If every Linux distribution fails, then I'm back to suspecting that a Windows driver is working with the hardware to keep it going, in a way that Linux is not able to do (without a comparable Linux driver), similar to my Toshiba NB205 situation.

---

### Post by sself on 2010-04-22
Yeah, that's kinda what I was thinking too. Bad news for me. I suppose I'll try to VM it through windows, but that's a crappy solution. I just can't shake the feeling that it's due to the multimedia haptic interface. No way to disable it in the bios. No way to do much of anything in the bios actually, it's really limited. I'll keep trying to figure it out. If I find a solution I'll be sure to post it and change the status. Maybe someone else will have this problem in the future. Thanks for the prompt response.

---

### Post by sself on 2010-04-22
OK, well I just tagged what's causing the lockup. I touched the multimedia volume control to turn the volume up. Now Notify-osd is going off, has been for 5 minutes straight now. It looks like it's in an infinte loop. Xorg jumped up to about 60% cpu cycles, notify-osd about 20% and compiz used up the rest. Had to ctrl-alt-backspace and things immediately calmed back down. There must be a way to disable the multimedia buttons on this laptop, I very rarely have ever used them. Any ideas, or an idea of a driver for something like that? I cannot interact with any windows or use type now, but the cpu is no longer locked up.

---

### Post by teqslamer on 2010-04-23
Not adding anything new but I am also having this same issue I have a Microsoft 'Natural' Ergonomic Keyboard model 4000 v1.0 which locks up often and the only way I can recover is to unplug then replug-in the keyboard which is not very user friendly.  If this is a problem with this type of USB keyboard I would really like to know.  Also like sself I have mouse usage during these lock up sessions.  I also dual boot into Window XP and it does not have this issue.

---

