---
title: "Unable to install Ubuntu 9.04"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by Dom83 on 2009-09-20
Hi everyone.
 
I've seen this problem a thousand times on forums but haven't found a solution that works for me.
 
I've completely erased all operating systems on my hard drive and am trying to install the most recent version of Ubuntu (9.04 I think). I've burnt a live CD which loads to the options screen from which I select either "Try Ubuntui without any change to your computer" or "Install Ubuntu"; both show the Ubuntu logo and loading bar for a short while and then I see a screen that says:
 
Loading, please wait...
 
BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built in commands.
 
(initramfs) _
 
The screen hangs and I can't get any further. I've had the same problem with version 8.1 but an earlier version (5 or 6?) worked ok, as did openSUSE (but I didn't like it so uninstalled it - I do tend to get a bit uninstall happy)
 
Any help to get this working would be massively appreciated as there is currently nothing on my computer and I think I might get in trouble if I keep using my girlfriend's laptop.
 
Cheers,
Dom

---

### Post by Shazaam on 2009-09-20
Hi Dom83 and welcome.
When you boot the Ubuntu 9.04 livecd, if you hit F4 or F6 you have a few things you can try to get the cd to boot. If all else fails re-burn the livecd as slowly as possible and try again.

---

### Post by yeats on 2009-09-20
I had this happen with the 64 bit Ubuntu and Kubuntu live CDs.  I ended up installing from a CD of Hardy 64 I had burned a while back and upgrading from there.

---

### Post by WatTwo on 2009-09-20
Yeah sounds like the disc is messed up, you can try burning another one, (like he said, slowest speed) or you can order one on ubuntu.com

I'm pretty sure its free to order one, just pay the shipping.

---

### Post by Dom83 on 2009-09-20
Hi Shazaam,
 
Many thanks for the swift response. I've tried each of the boot options and none changes the outcome. I have also tried burning slowly (this was suggested on one of the other threads that I read) but with no success. 
 
Do you know if there's any way that I could diagnose what the problem is? It must be some addition to the OS that wasn't there in earlier versions and isn't in openSUSE 11.
 
Cheers,
Dom

---

### Post by Dom83 on 2009-09-21
Hi everyone.
 
Thanks for the help. The issue I have with upgrading once installed is that I can't get my wireless working (one of the reasons I was trying a more recent version!). If anyone has any other suggestions it'd be hugely appreciated.
 
Thanks

---

### Post by raymondh on 2009-09-21
> **Dom83 said:**
> Hi everyone.
 
Thanks for the help. The issue I have with upgrading once installed is that I can't get my wireless working (one of the reasons I was trying a more recent version!). If anyone has any other suggestions it'd be hugely appreciated.
 
Thanks

Assuming your system meets the requirements ...

On installation issue:

1.  Check if MD5 matches
2.  Check CD for defects (one of the options in the liveCD)
3.  Failing a F4 safe-graphics-mode, you can try an [alternate install]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").  If you do, download from a torrent which will check the MD5 for you.

On wireless issue :

It depends on the actual error.  It may simply be a driver that needs to be activated or, a driver that needs to be downloaded from the manufacturers' site.  Or, some members have even used ndiswrapper (using a windows-based driver).  The sticky/s on the wireless subforum should start giving you clues.

Have you tried a liveSession (try ubuntu without any changes)?  Also, when you do install, and if possible, try to hook up through ethernet cable in the meantime while you troubleshoot the wireless issue (as well as do your first update).

Back-up your files.  Good luck.

Regards.

---

