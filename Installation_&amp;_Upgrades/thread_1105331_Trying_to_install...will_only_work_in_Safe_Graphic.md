---
title: "Trying to install...will only work in Safe Graphics Mode"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by richg813 on 2009-03-24
Hello Everyone, I'm new to the group.

I have my 8.10 cd, I installed it on one computer alongside Windows, it works like a dream (super fast really).

On my other pc, my main pc, I've tried installing it alongside Windows.  When I reboot and choose ubuntu it looks like it will boot and brings up the signature background but immediately after the window that pops up saying "Checking Installation" with all differently colored pixels in and around the window, the system just hangs and hangs and hangs.

Thinking it might be my grapic card nvidia geforce 7800 GT, i tried booting from the cd, hitting F4 and selecting Safe Graphics Mode.  This is the only way the cd will boot into cd-based ubuntu.

I really want to run from my hard drive.  Any ideas?

What is "Safe Graphics Mode"?  Will I always have to run that way?  Is there a way to modify the hard drive installation to boot into Safe Graphics Mode (only an option when cd booting).

I know these are alot of questions, but please have patience with the newbie (me).

Thanks for your consideration,
Rich

---

### Post by hockeyhead019 on 2009-03-24
i would think because your graphics card is nvidia you will need to download the proprietary drivers. 

System -> Administration -> Hardware Drivers

then it should give you the compatible nvidia drivers and then you can download them and then you might be able to go to 

System -> Preferences -> Appearance and change the effects column... 

idk honestly if that will solve your problem but it's worth a try

---

### Post by markbuntu on 2009-03-24
You should boot from grub into the recovery kernel and then choose the xfix option and then continue. This should give you a normal boot and get you to the gui with the VESA driver. Once you get there run update manager and get all the updates. Reboot and then try to use any proprietary/restricted driver you need. You need all the updates for the restricted driver to install and run properly.

---

### Post by richg813 on 2009-03-25
I GOT IT TO WORK!  WOHOOOO!

This is what I had to do:

1. Installed 64-bit ubuntu within Windows.
2. Reboot
3. Choose to boot into ubuntu instead of Windows.
4. You then have 10 seconds to hit esc to enter "Menu"
5. I chose the "Safe Graphics Mode" option.
6. It then boots fine into ubuntu in Safe Graphics Mode.

It then does some more installing and automatically reboots

7. Choose to boot into ubuntu instead of Windows.
8. You then have 10 seconds to hit esc to enter "Menu"
9. I chose the "Safe Graphics Mode" option.
10. It boots fine into ubuntu

11. I then downloaded the proprietary Nvidia driver by clicking:
System -> Administration -> Hardware Drivers

12. It then wants you to reboot, I did and didn't have to select anything, it booted great!

Thank-you everyone!

Rich

---

