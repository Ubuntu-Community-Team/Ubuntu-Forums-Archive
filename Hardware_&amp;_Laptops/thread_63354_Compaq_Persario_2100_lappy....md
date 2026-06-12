---
title: "Compaq Persario 2100 lappy..."
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by Teegee on 2005-09-07
On this laptop i just installed Ubuntu 5.04.  I'm guessing thats Hoary Hedgehog 5.04.  After installing this, I reboot, and the LCD comes on during BIOS and text part of boot up, then shuts off once the GUI is supposed to load.  I found a thread on here that seems to issue the problem, but no response was ever made.  Any help would be great. Thanks.

---

### Post by mlomker on 2005-09-07
[QUOTE=Teegee]On this laptop i just installed Ubuntu 5.04.  I'm guessing thats Hoary Hedgehog 5.04.  After installing this, I reboot, and the LCD comes on during BIOS and text part of boot up, then shuts off once the GUI is supposed to load.  I found a thread on here that seems to issue the problem, but no response was ever made.  Any help would be great. Thanks.[/QUOTE]

It probably isn't liking the automatically detected video card.  Start up in recovery mode (press ESC at the grub prompt and select the recovery kernel).  Log in and edit the /etc/X11/xorg.conf file.  Look for the **Section "Device"** section and change the **Driver** to vesa.  It might be set to ati or something else that isn't quite compatible.

You could search Google as well...saw plenty of references to loading other linux distros on that model.

---

### Post by emperor on 2005-09-07
Looks like the ati hardware ( ATI IGP 340 Graphics card 64MB shared) requires the older "radeon" video driver. 

See this guys xorg.conf file: [http://www.priller.co.uk/xorg.conf](http://www.priller.co.uk/xorg.conf)

Also this link for full report on your lappy and linux:
[http://www.priller.co.uk/compaq2100.html](http://www.priller.co.uk/compaq2100.html)
[http://www.linux-on-laptops.com/compaq.html](http://www.linux-on-laptops.com/compaq.html)

---

### Post by Teegee on 2005-09-08
Well, I'm a real noob at Linux.  I can start it up in recovery mode, but I don't know how to edit the file from there.  Also, I can boot up the laptop and plug in a external monitor in the back and view Linux on that monitor.  So technically, I can see it running.  But I have no idea how to edit the file from there either.  The texteditor won't let me edit it.

---

### Post by kagashe on 2005-09-09
[QUOTE=Teegee]Well, I'm a real noob at Linux.  I can start it up in recovery mode, but I don't know how to edit the file from there.  Also, I can boot up the laptop and plug in a external monitor in the back and view Linux on that monitor.  So technically, I can see it running.  But I have no idea how to edit the file from there either.  The texteditor won't let me edit it.[/QUOTE]
 Hi,

Open the editor by sudo command:
> sudo gedit /etc/X11/xorg.confand it will allow you to edit.
Only sudo (root user) can edit config files.

kagashe

---

### Post by atrus325 on 2005-09-09
Does this use the ATI XPress 200m?  If so, I got it working under Gentoo using an older driver.  I imagine it'd be the same for Ubuntu.

Edit: checked your exact card, and this ain't it.  Sorry for the premature post.

J.

---

### Post by Teegee on 2005-09-09
Ok, well we have a bigger problem now.  I fixed the file and rebooted.  The login screen came up fine on my laptop screen.  However, once i login everything passed that point is distorted, it looks as if the whole screen has been chopped into diagonal pieces and compressed.  I couldn't recognize anything. Help!!

P.S. In the time I've been able to work some with Linux I like it. I just want it to work! =P

---

### Post by emperor on 2005-09-10
What did you set the Horizonal and Vertical refresh to in xorg.conf?

The example on linux laptops at the following:

Section "Monitor"

    Identifier  "My Monitor"

    HorizSync   31.5-48.5

    VertRefresh 40-70

    vendorname "[My Monitor]"
    modelname "[My Monitor]"
EndSection

---

### Post by Teegee on 2005-09-11
I don't see that section.  The one I found similar to it just had Identifier and Opinion I believe.

---

### Post by emperor on 2005-09-12
I would suggest you run "xorgconfig" and let it guide you in creating a new xorg.conf file. (Save the current one first!)

cd /etc/X11
sudo cp xorg.conf xorg.conf.orig

sudo xorgconfig

Note: if an error occurs in finding xorgconfig, you will need to find it and specifiy the location of the utility. For examlple:

/local/X11R6/xorgconfig  

You can use locate to find xorgconfig. For example:

sudo updatedb
sudo locate xorgconfig

Note: It is best to generate this file from a terminal in runlevel 3 (no xserver runnning!). You can use the alternate grub entry to boot in maintance mode, but you should set a root password first, then you can login as root (no sudo use in this case!).

---

