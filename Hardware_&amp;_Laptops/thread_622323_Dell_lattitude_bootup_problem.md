---
title: "Dell lattitude bootup problem"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by painterh on 2007-11-24
I just reinstalled ubuntu feisty on my old Dell laptop.  All was working fine so I upgraded to Gutsy using update manager.  I thought it was strange when it said that update manager closed unexpectedly when not quite finished with upgrade.  When I restarted my computer, It seemed as if everything went OK until I selected the new kernal from grub and proceeded to boot.  I came to a point where it said "starting nfs services" and just hung there.  I tried 'ctrl/alt/del, and ctrl/alt/backspace and nothing worked.  I then powered off using power button.  Now every time I try to boot up (no matter which kernel I try or recovery mode, it just hangs in that same place.  Anybody know what's going on.  The machine is a Dell Latitude CPXj gt750 with 512 megs ram and a d-link 650+ wireless pcmcia card, and a usb notebook mouse.

---

### Post by tomauty on 2007-11-24
Yeah mine is stuck there too.

---

### Post by painterh on 2007-11-24
What laptop do you have?  Mine seemed to do ok with feisty, but something went wrong when upgrading to Gutsy. I did have a little trouble with wireless connection.  I would be on the net and suddenly no connection.  I was thinking it was connected to a wireless issue or possibly something else.  I only started with Ubuntu and Linux in general since March 07.  I have my desktop and this laptop both setup as dual boot with Linux and WinXP.

---

### Post by painterh on 2007-11-24
Just a note. I tried again to boot up my Dell about a half hour ago and left at the point of hanging, and the only thing I noticed in the text display was a line which said "$Loading AppArmor module: Failed"

---

### Post by tomauty on 2007-11-24
I don't have a laptop but I rebooted my computer and it hung at that, and this was the closest thread I could find that had the same problem.

---

### Post by painterh on 2007-11-24
My desktop runs great with ubuntu.  It took me a while to get beryl and a few things working but no complaints.  My laptop is a different story.  The first time I tried to install, apparently the wrong video driver got configured and during boot up when it got to loading graphical display it just went to a sort of blank screen with some sort of smudged colors.  I never got that sorted, so I re-installed, and now this issue with bootup.

---

### Post by painterh on 2007-11-24
OK.  I just tried to bootup without my wireless card installed and was successful.  Apparently my card has issues.  II tried using ndiswrapper to install the windows drivers but it wouldn't recognize my card.  I might to have to mess with this a while.  If anyone knows how to install and configure different drivers for a D-link AirPlus 650+ wireless card, I would appreciate the help.

---

### Post by slowpoke115 on 2008-04-15
ndis wrapper is rubbish, download and install madwifi. The trunk download should sort mmost of your problems. In regards to configuring it, well thats a different question :P

[http://snapshots.madwifi.org/](http://snapshots.madwifi.org/)

---

