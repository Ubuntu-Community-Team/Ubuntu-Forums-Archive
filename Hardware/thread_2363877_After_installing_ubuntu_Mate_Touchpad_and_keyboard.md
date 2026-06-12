---
title: "After installing ubuntu Mate Touchpad and keyboard stopped working on win7"
date: 2017-06-15
forum: Hardware
---

### Post by omanzanilla on 2017-06-15
i you all! this is my first post in the forum. I am a newbie in Linux matters, but I try to solve things by myself following the forums as much as I can. However, for this problem I have not been successful:

I had previously in my laptop (LENOVO SL400, 64bits) dual boot for Windows 7 and Ubuntu 16.04 (Win7 was installed first). This worked without problems. I tried upgrading to more recent LTS versions, but the process finished abruptly and I was left without a properly working linux distro. It was completely broken. I could, however, use normally Win7 (no mouse, touchpad or keyboard issues, which leads me to conclude that this is not a "windows problem").

I created my ISO with Ubuntu MATE 16.04 LTS (I decided to try the MATE desktop), and it was installed without problems. The madness began when I rebooted and tried to go to Windows 7 again. Neither keyboard nor touchpad worked. I plugged in a USB keyboard and a USB mouse (which already worked with the MATE recently installed), and only the mouse allowed me to interact with win7.

I want to stress the point that touchpad and keyboard were working perfectly with  Win7 before installing MATE. Also, keyboard works perfectly in the BIOS, and the GRUB, as well as in Ubuntu MATE.

I will now list the things I have tried (sorry for writting a long post ,but I think the right thing to do is to give as much detail as I can):

1) In the window where you can see the properties of the keyboard, which was listed as "hardware with problems" or something on those lines, I could read a message that said the following: "Windows cannot start this hardware device because its configuration data (in the Registry) is incomplete or damaged (code 19)". ->This is a translation from spanish.. so it might not be the exact wording in english. I went through the forums and followed the instructions to fix the "code 19" error for keyboard, which consisted in going to the registry, locating the folder of the "keyboards", and deleting a "LowerFilter" or "UpperFilter" thing, which I did. I re-booted, and it didn't work (I used the keyboard on the screen with the mouse to do these things, from the Accessability options).

2) I tried to update the controllers, looking for a newer version online. Didn't work. When trying to look at the controllers in disk, it said that it had already the most up-to-date controller for the device.

3) I tried going to the BIOS and setting everything with the default values, saved and continued booting. It didn't work.

4) In one forum, someone who had a similar problem, "solved" the problem installing VMware over Ubuntu, and installing Win7 in a Virtual Machine. I don't think I would like to do this, as I had a working Windows already.. and my machine is not abundant in resources, so running win7 over a VM does not seem like a good idea in terms of performance for an old laptop.

5) I followed another thread where they solved the problem disabling the "Legacy USB" option in the BIOS. I don't have that exact option, but I have one that controls if it is possible to boot from a USB device or not... and I disabled it. It didn't work. 

Please, forgive me if I have not followed the guidelines and rules properly... of the forum, I mean... and if I missed some answer to this problem. I looked in the search bar for this issue, but didn't find any pertinent result.

Hope you can give me some ideas to try... specially if they do not involve re-installing Windows!

Orestes

---

