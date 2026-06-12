---
title: "Inspiron 1520 W/Gutsy wireless"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by spliner on 2007-10-08
Has anyone had luck getting wireless to work using the Broadcom 1390 wireless card from Dell on the Inspiron 1520?  I'm using the Gutsy beta, and I am somewhat of a newb.  I've been running Ubuntu in VMWare for quite a while now.  This is my first full install as a dual boot Vista/Ubuntu system.

I've tried several guides with no luck.  The wireless light will come on but the interface does not show up.  I have the latest ndiswrapper (1.48) and have downloaded the WinXP 32 bit driver for the 1520 (BCM151520.exe) and tried compiling the driver but I get errors.

I don't suppose someone who's gotten it working would post a guide for the Gutsy instructions.  The error I get is "wrong driver", and none of the guides I have seen tell me exactly which driver to download from Dell for the 1520.  Should I have downloaded the Vista driver or another OS for this method to work properly?

Thanks in advance.. and yea before anyone yells at me, I know I shouldn't be running the Gutsy beta as a newb, but I am learning here and don't mind working for it.  I could use a bit of help though!  ;)

Spliner

---

### Post by ~chinook~ on 2007-10-08
You need to plug into the internet and sudo apt-update. Then go into system-advanced restricted drivers and enable the broadcom adapter.

---

### Post by spliner on 2007-10-08
That was easy.. now.. why did it stop working and the interface dissapear when I rebooted?

---

### Post by spliner on 2007-10-09
I'll keep sifting through other posts, but I can confirm that the interface dissapears after a reboot.  Disabling and re-enabling the restricted driver seems to bring it back.  The hard switch is on (on the side of the laptop) so that doesn't seem to be the problem.  At this point I will likely just wait until the final release of 7.10 and do a re-install, however just wanted to spend some free time working on it.

Thanks again,

Spliner

---

### Post by cubeist on 2007-10-09
OK, first, enable the restricted driver in gutsy, then follow this tutorial word for word...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

and you should have working wireless... That tutorial has worked for me on several different occasions in both feisty and gutsy...

edit **
I just had an afterthought ... in your /etc/network/interfaces file, try commenting out everything except the first two lines, which should be:
auto lo
iface lo inet loopback

to do this... backup your interfaces file with:  "sudo cp /etc/network/interfaces /etc/network/interfaces.orig"
then type: "sudo nano etc/network/interfaces"  to gain access to the file

end edit **

---

### Post by spliner on 2008-03-23
> **cubeist said:**
> 
edit **
I just had an afterthought ... in your /etc/network/interfaces file, try commenting out everything except the first two lines, which should be:
auto lo
iface lo inet loopback

to do this... backup your interfaces file with:  "sudo cp /etc/network/interfaces /etc/network/interfaces.orig"
then type: "sudo nano etc/network/interfaces"  to gain access to the file

end edit **

Hey!  That worked.  I had given up on this a long time ago, and had just been using a wired connection.  Tonight I followed this guide again:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Then I followed your instructions above.  I can now click on the icon at the top, select a connection and my wireless is up and running!  Thanks!!!

-Spliner

---

