---
title: "Change Screen Resolution on 14 running on VirtualBox"
date: 2015-12-17
forum: Hardware
---

### Post by Steve_Cline on 2015-12-17
I am trying to increase resolution so I can see the bottom of my popup boxes and decrease Icon size on the launcher.

I am running on VB 14.04.  When I put in xrandr to terminal I get:

Screen 0: minimum 64 x 64, current 1092 x 530, maximum 32766 x 32766
VGA-0 connected primary 1092x530+0+0 0mm x 0mm
   1092x530       60.0*+
   2560x1600      60.0  
   2560x1440      60.0  
   2048x1536      60.0  
   1920x1600      60.0  
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      60.0  
   1024x768       60.0  
   800x600        60.0  
   640x480        60.0  

Using xrandr -s to change resolution does not seem to change this.  The proportions of the screen change but not the icon sizes or what fits on the screen.  Am I using the correct command?

---

### Post by v3.xx on 2015-12-17
Have you installed the extension pack (guest additions)?

I do not run Unity desktop, but I think icon size is fixed.

---

### Post by Steve_Cline on 2015-12-17
I think I did that a while back.  How would I know?

---

### Post by v3.xx on 2015-12-17
The last post in this thread.

[http://askubuntu.com/questions/169024/how-can-i-tell-if-the-virtualbox-guest-additions-were-installed-on-an-ubuntu-vm](http://askubuntu.com/questions/169024/how-can-i-tell-if-the-virtualbox-guest-additions-were-installed-on-an-ubuntu-vm)

---

### Post by v3.xx on 2015-12-17
Here's my guest output

```
~$ lsmod | grep -i vbox
vboxsf                 49152  2
vboxguest             286720  7 vboxsf
vboxvideo              16384  1
drm
```

Also be sure the package "virtualbox-guest-dkms" is installed.

---

### Post by Steve_Cline on 2015-12-17
Here are my results:

vboxsf                 42570  0 
vboxvideo              12578  1 
drm                   244037  2 vboxvideo
vboxguest             223958  6 vboxsf

Does that mean virtualbox-guest-dkms is not installed?

---

### Post by v3.xx on 2015-12-17
To check the guest dkms run the following terminal command:

```
sudo apt-get install virtualbox-guest-dkms
```

If it is already installed, it will say so.  If it installs, then a restart of the guest is required.

Also you could try another desktop for testing purposes.

```
sudo apt-get install gnome-panel
```

This will install the "Flashback" desktop.  To switch desktops, at the login screen click on the icon and choose Flashback (metacity).

---

### Post by Steve_Cline on 2016-01-03
Thank you for the advice.

Guest dkms is installed.

The "Flashback" desktop had the effect of decreasing the size of the icons but I still cannot see the bottom of my pop-up boxes.  For example, when opening a settings window the buttons at the bottom are inaccessible, even when maximizing the window.

---

