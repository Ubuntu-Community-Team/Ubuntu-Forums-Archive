---
title: "[SOLVED] Black screen on ATI card after intrepid upgrade"
date: 2008-11-02
forum: Hardware
---

### Post by ploum on 2008-11-02
Hello,

My father was using Ubuntu 8.04 on his desktop PC with an ATI graphic card and a widescreen. In order to have the correct resolution for its 16:9 widescreen, I installed fglrx with envy-ng.

Yesterday, I upgraded him to 8.10. The upgrade was smooth without any problem but now, after a reboot, his screen is black !

It's very strange because GDM is running (when can hear the "tudum" starting sound) and there is no error in the X.log. But the screen is black (the screen says "no signal").

I tried to remove /etc/x11/xorg.conf file (it did the trick on my laptop with an ATI card too) but nothing change. Still black screen an no error.

I have absolutely no idea on how to solve this problem. I didn't find any similar bug on launchpad (all black screen errors are related to an error or a driver crash). 

Any help or advice will be greatly appreciated :-)

Thanks

---

### Post by teaker1s on 2008-11-02
Only if it ran successfully without accelerated graphics previously:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

the above command will effectively remove restricted driver from use in current xorg.conf from my experience.

you then could have a look in the restricted driver section or use envy to reinstall the driver.

---

### Post by ploum on 2008-11-02
thanks for the reply. Unfortunatly, it doesn't change anything : still the black screen and the "tudum" sound of GDM...

---

### Post by nikem on 2008-11-02
try this it worked for me a couple minutes ago.

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by ploum on 2008-11-02
For the record, the bug is in the ATI open source driver :
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/273510](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/273510)

When upgrading from Hardy to Intrepid, Intrepid automatically disable fglrx and switch to the open source ati driver. You then have the bug.

The fix is to reinstall the fglrx proprietary driver. apt-get install xorg-driver-fglrx should be enough but here's the procedure I've followed :

1) Configure X.org to use the vesa driver :
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
(I didn't find any easy way to do that in an easier way)

2) Restart GDM and login :
sudo /etc/init.d/gdm restart

3) In the configuration option, choose "hardware driver". If you don't have it, install jockey-gtk.

4) Enable the ATI proprietary driver.

5) It should work..

---

### Post by cnr437 on 2008-11-02
There is the same problem at my computer too, GDM logins and tutumms sound came also screen can be seen but in very black constrast with black screen.

so ploum, can you repeat steps as explaining with a little more details pls?

should I change "fglrx" into "vesa" in xorg.conf?

Do I need to select and active "ATI restricted ....." after changed fglrx into vesa and restarted gdm? Wont 'activating that proprietary driver' change 'xorg.conf' file again?

Sorry for stupid question :) but I have really serious headache now :(
Thanks for your interest.

---

### Post by cro on 2008-11-03
I had this problem, and found that there were old kernel modules installed.

In a terminal, type 'dkms status', and check the list. If any module listed has a kernel number other than your current kernel, then disable it.

For example, I had vboxdrv installed (Sun Virtualbox), which conflicted with X. Disabling vboxdrv solved all the X crash problems.

---

### Post by cnr437 on 2008-11-03
:(

---

### Post by ploum on 2008-11-04
cnr437 > 

1) sudo apt-get install xorg-driver-fglrx
2) sudo rm /etc/X11/xorg.conf
3) sudo /etc/init.d/gdm restart

This might be enough if you have a network connection while in commande line. This install the restricted driver but I didn't tested this way.

If the above method doesn't work, try this :

1) sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
2) sudo /etc/init.d/gdm restart

At this point, you should login but you will be using the VESA driver (poor performances and probably bad resolution).

3) Go to System > Administration > Hardware drivers
(you should have the jockey-gtk package installed)
4) Enable the ATI proprietary driver
5) Reboot


Don't bother about xorg.conf. The new X by default doesn't use xorg.conf and try to find the best solution. The problem is that, if the proprietary driver is not installed, the best solution should be the ati opensource driver. Unfortunatly, it is buggy with this card.

---

### Post by cnr437 on 2008-11-04
I tried these but still screen is black at login started gdm
it was better at old X :(

fglrxinfo
----------
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

I can login with fixing X by recovery. But I really didnt understand why it happened bad to old ati drivers. Cant they solve this problem?

---

### Post by krusbjorn on 2008-11-04
I had the problem with the black screen too, although I have turned my sounds off so I dont know if gdm started or not. Anyways, the solution was to unplug my TV. I dont know why, but both my TV and monitor turn pitch black when X starts as long as the TV is connected to the computer.

---

### Post by Fraser67 on 2008-11-04
So how do you disable a module that is linked to an old kernel?

---

### Post by mnk0 on 2008-11-05
cnr437 .. yeah im having the exact same issue as u.

---

### Post by eti.que on 2008-11-08
> **ploum said:**
> For the record, the bug is in the ATI open source driver :
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/273510](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/273510)

When upgrading from Hardy to Intrepid, Intrepid automatically disable fglrx and switch to the open source ati driver. You then have the bug.

The fix is to reinstall the fglrx proprietary driver. apt-get install xorg-driver-fglrx should be enough but here's the procedure I've followed :

1) Configure X.org to use the vesa driver :
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
(I didn't find any easy way to do that in an easier way)

2) Restart GDM and login :
sudo /etc/init.d/gdm restart

3) In the configuration option, choose "hardware driver". If you don't have it, install jockey-gtk.

4) Enable the ATI proprietary driver.

5) It should work..

Salut Ploum,

Just wanna thank you for that. I was really struggling to get my 780G (HD3200) working with Intrepid, and your message made the trick.

Cheers!

---

### Post by cnr437 on 2008-11-08
I didnt enable proprietary driver yet after this I had black screen issue and now I use default driver and options on my box after setup.

glxinfo
---------------------
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
.......
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.2

I hope ati and cononical will come across and solve this problem as soon as possible.
I want to use my graphic card efficiently :P :)

---

