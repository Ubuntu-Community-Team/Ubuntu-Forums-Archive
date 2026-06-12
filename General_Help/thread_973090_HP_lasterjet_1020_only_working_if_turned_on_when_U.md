---
title: "HP lasterjet 1020 only working if turned on when Ubuntu starts"
date: 2008-11-06
forum: General Help
---

### Post by Morientes on 2008-11-06
I have an HP 1020 lasterjet printer. It has traditionally been hard for me to make it work. I used to be able to make it work using the foo2zjs driver: [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) .
However now it only seems to work if the printer is turned on when Ubuntu starts (I am using Ubuntu 8.10).
Any ideas as to what I can do. There must be some command that can make Ubuntu think the printer was turned on when starting up...

---

### Post by der_joachim on 2008-11-07
In Intrepid, I configured my HP1020 with the HPLIP drivers. It does basically do the same thing as the foo2zjs driver: it downloads a new firmware version, and flashes the printer. 

Configuring it is quite an easy job, even easier that compiling foo2zjs:
```

sudo -s
aptitude install hplip
hp-setup

```

Follow the on-screen instructions and you're set.

One caveat though: AFAIK, the hplip package is installed by default, so you may get an error message when trying to install hplip.

---

### Post by Morientes on 2008-11-07
Thanks a lot for the reply. I had already tried the hp-setup but this time I tried it with the GUI installed and it prompted me to download the plugin for the printer which it had not done before so I was a little excited.
However it did not work, unfortunately. When I try to print I get this error in dmesg:
```

[ 1351.790091] type=1503 audit(1226076977.588:21): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=8092 profile="/usr/sbin/cupsd"
[ 1356.852036] usb 2-2: usbfs: USBDEVFS_CONTROL failed cmd hpijs rqt 161 rq 1 len 1 ret -110

```
Any idea what that might be about?

---

### Post by Morientes on 2008-11-07
I have a little more information. As always the printer works if it is turned on when Ubuntu boots up. If I switch off the printer and then turn it on again, I get this in dmesg, though:
```

[  371.410838] usb 2-2: USB disconnect, address 3
[  386.336012] usb 2-2: new high speed USB device using ehci_hcd and address 8
[  386.488686] usb 2-2: configuration #1 chosen from 1 choice
[  386.492060] usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17
[  389.614042] usblp0: removed
[  395.796113] usb 2-2: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -110

```
So something happens that removes the printer again after it is setup (the last two lines). Anyone has an idea what it might be?

---

### Post by dudous on 2008-11-08
I was having a weird behavior too.
Sometimes i turned it on or off to work. Or i noticed that my requests were executed slowly.
I executed hp-setup again, remove the old printer icon and set the new one as the defalt printer (System -> Administration -> Printers) . Aparently it worked for me.

---

### Post by Morientes on 2008-11-09
Thank you for the suggestion.
Reinstalling using hp-setup does not help in my case unfortunately.
Any other ideas?

---

### Post by Morientes on 2008-11-09
Hm, I have just found out that when the printer is not working, I can now delete it and then run sudo hp-setup and then it will work again. In this way I don't have to restart so it is definitely a better solution.

I would still like to have it working when I turn the printer on without having to run hp-setup every time, since that is a bit annoying.
Therefore, any ideas are still very welcome!

---

### Post by dudous on 2008-11-09
Well, here it goes another suggestion:

1- Right click HPLIP status service icon (HP Purple icon)
2- Click "HP Device Manager..."
3- Click on the Configuration menu
4- Click on "Configuration (F2)" or type F2
5- Mark the CheckBox to activate automatic updates... 
   (30 seconds is the default)

This has to be done to other users if you have it.

After that, choose the "Printer control"tab and see if there is a button named "start printer" and in this case, click it to start the printer.

I don't know if this will solve the problem.
I'm still testing while a write this post...

---

### Post by dudous on 2008-11-12
Well, i´m with printer problems yet. The same problem as Morientes.
I tried to download and install the last hplip version from his page, but it also don´t work for me.
If someone know how to solve this question or also a workaround, please share with us.

---

### Post by dudous on 2008-11-25
Has someone solved this problem ?

---

### Post by azr on 2009-01-15
I'm also struggling what could be a similar problem. My suggestion, though not a solution, is run

```
hp-check
```

(If you have hp manager installed). It will likely show at the end of it's out put how many errors it found - scroll back up to read what they're about.

As for me, if i can't get the printer to work with the hp-manager I'm going to remove it and install the printer's drivers manually with these simple instructions (with which i had previously got it to work):
[http://www.linuxhaxor.net/2008/01/10/installing-hp-laserjet-1020-on-ubuntu/]("Installing HP laserjet 1020 on ubuntu")

---

### Post by azr on 2009-01-15
I'm also struggling what could be a similar problem. My suggestion, though not a solution, is run

```
hp-check
```

(If you have hp manager installed). It will likely show at the end of it's out put how many errors it found - scroll back up to read what they're about.

As for me, if i can't get the printer to work with the hp-manager I'm going to remove it and install the printer's drivers manually with these simple instructions (with which i had previously got it to work):

[http://www.linuxhaxor.net/2008/01/10/installing-hp-laserjet-1020-on-ubuntu/]("Instructions here")

---

### Post by todak on 2009-01-15
According to [http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html) 

[B]Driver Plugin Information:

This printer REQUIRES a downloadable driver plug-in. Use hp-setup to install the printer, and to download and install the plug-in. In general, required driver plugins are required for printing support. Driver plug-ins are released under a proprietary (non-open) license and are not part of the HPLIP tarball release.[/B]

---

### Post by markovg on 2009-01-21
While simply plugging in my HP 1020 seemed to detect it and set it up fine.  It did not respond to any print jobs, though CUPS showed the jobs as completed.

I was able to get my HP 1020 to print on xubuntu intrepid with the following process:

1) $ sudo apt-get install hplip-gui

2) Remove the printer via [http://localhost:631](http://localhost:631) or (xubuntu settings->printing)

3) Install the printer with
$ hp-setup

4) Run the HPLIP toolbox in Admin or Settings menu

5) Go to the actions tab for your printer and "Download Firmware"

The printer awoke, and would print test pages.

The HPLIP toolbox claims that "Download Firmware" is "required on some devices after each power-up".  

Perhaps a firmware download would help to get your 1020 working if turned on after Ubuntu startup?

---

### Post by Sprax on 2009-01-22
YES! It works, brilliant! You should repost this so people don't miss it. Actually I might as well do it.

Thanks!

> **markovg said:**
> While simply plugging in my HP 1020 seemed to detect it and set it up fine.  It did not respond to any print jobs, though CUPS showed the jobs as completed.

I was able to get my HP 1020 to print on xubuntu intrepid with the following process:

1) $ sudo apt-get install hplip-gui

2) Remove the printer via [http://localhost:631](http://localhost:631) or (xubuntu settings->printing)

3) Install the printer with
$ hp-setup

4) Run the HPLIP toolbox in Admin or Settings menu

5) Go to the actions tab for your printer and "Download Firmware"

The printer awoke, and would print test pages.

The HPLIP toolbox claims that "Download Firmware" is "required on some devices after each power-up".  

Perhaps a firmware download would help to get your 1020 working if turned on after Ubuntu startup?

---

