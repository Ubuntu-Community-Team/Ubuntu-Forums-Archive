---
title: "Cannot browse bluetooth phone with OBEX anymore"
date: 2008-08-01
forum: General Help
---

### Post by cyran on 2008-08-01
I only connect my phone sparingly, so I can't be sure if the upgrade to Hardy might be responsible. I only know this was working fine in February, and was broken in May. (I upgraded just after release day.)

I have an LG CU500 phone, that I've managed to use both as a tethered internet connection and as an OBEX ftp server. The first thing is still working the same, but the second thing isn't.

I've accessed my phone's files in the past with the gnome-vfs-obexftp package, and clicking 'Browse Device...' from the Bluetooth Applet (the [www.bluez.org](www.bluez.org) one). That opens obex://[00:19:A1:zz:zz:zz] in Nautilus, which used to list all the files set on my phone to be available over Bluetooth. Now it just gives the error:

> **The folder contents could not be displayed.**

Operation failed (unexpected response)

Entering 'sdptool browse' on the command-line only says one line, "Inquiring ..." and then it apparently gives up.

I can still access my phone's files via Windows XP's Bluetooth Places, so I know it's still working on some level. But I don't have access to another bluetooth phone to test with Ubuntu.

Can anyone help me figure out what's gone wrong?

---

### Post by fragos on 2008-08-02
Install "blueman" and "bluetooth" packages. Blueman will help you more easily deal with things like bluetooth pairing. The bluetooth package will insure you have the bluez bits you'll need.

---

### Post by cyran on 2008-08-20
> **fragos said:**
> Install "blueman" and "bluetooth" packages. Blueman will help you more easily deal with things like bluetooth pairing. The bluetooth package will insure you have the bluez bits you'll need.
I have the 'bluetooth' package already. I think that's where the Bluetooth Applet came from. As for blueman:  [You mean this thing?](https://launchpad.net/blueman) Just FYI, it's not in the Hardy repositories--I almost thought you meant 'bluemon,' which was the closest thing, when I looked there.

I'll edit after I try blueman.

EDIT: Okay, that failed spectacularly. The Browse function in Blueman just opens the *exact* same obex://mac-address URI in Nautilus.

---

### Post by fragos on 2008-08-20
> **cyran said:**
> I have the 'bluetooth' package already. I think that's where the Bluetooth Applet came from. As for blueman:  [You mean this thing?](https://launchpad.net/blueman) Just FYI, it's not in the Hardy repositories--I almost thought you meant 'bluemon,' which was the closest thing, when I looked there.

I'll edit after I try blueman.

EDIT: Okay, that failed spectacularly. The Browse function in Blueman just opens the *exact* same obex://mac-address URI in Nautilus.

That is the package I referred to. Do you have the universe and multiverse packages checked in "Software Sources"?

---

### Post by cyran on 2008-09-01
Yes. [blueman's not in Hardy at all](http://packages.ubuntu.com/hardy/blueman). It's [still just getting packaged](https://bugs.launchpad.net/ubuntu/+bug/164023) for Intrepid-or-later.

Not sure how it could help if the problem's at or below the Nautilus / Obex-FTP level.

---

### Post by fragos on 2008-09-01
> **cyran said:**
> Yes. [blueman's not in Hardy at all](http://packages.ubuntu.com/hardy/blueman). It's [still just getting packaged](https://bugs.launchpad.net/ubuntu/+bug/164023) for Intrepid-or-later.

Not sure how it could help if the problem's at or below the Nautilus / Obex-FTP level.

When I do a synaptic search I get blueman version 0.5-0ubuntu1 which is how I installed it. I download from the US and not the Main server if that makes a difference.

---

### Post by livia on 2009-01-07
Try this [https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/283064]("https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/283064"). Do what this guy Onkar Shinde said.
[https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/283064/comments/1]("https://bugs.launchpad.net/ubuntu/+source/obex-data-server/+bug/283064/comments/1")
I was unable to browse my mobile phone but, after installing the **gnome-user-share** package and set up like he suggested and after a REBOOT of the system, everything is working know and I can browse my phone files.

---

### Post by munishvit on 2012-11-22
> **cyran said:**
> I have the 'bluetooth' package already. I think that's where the Bluetooth Applet came from. As for blueman:  [You mean this thing?](https://launchpad.net/blueman) Just FYI, it's not in the Hardy repositories--I almost thought you meant 'bluemon,' which was the closest thing, when I looked there.

I'll edit after I try blueman.

EDIT: Okay, that failed spectacularly. The Browse function in Blueman just opens the *exact* same obex://mac-address URI in Nautilus.

Bluetooth Manager (blueman) was helpful to me as well. Thanks.:)

---

### Post by wildmanne39 on 2012-11-22
Old thread closed.

---

