---
title: "Vbox Guest Additions Not Working in 9.04"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by OswaldGlinkmeyer on 2009-05-08
Using Xubuntu in Sun xVM VirtualBox.  Attempted to upgrade to 9.04 from within Xubuntu, after rebooting could not get it to boot up.  

Instead, attempted to upgrade from 9.04 .iso file.   This time was able to boot in 800x600, but was not able to install Vbox Guest Additions, even though they were working in 8.x.  When I reboot I get message:[INDENT][FONT=Courier New](EE) Failed to load module "vboxvideo" (module does not exist, 0)[/FONT]
[FONT=Courier New] (EE) No drivers available.[/FONT]
[/INDENT]So, then I decide to create a new virtual machine from scratch.  Again, same results.  Works in 800x600, but after I install Vbox Guest Additions, I get the above error.  Then after several reboots I am able to boot, just never go over 800x600.

There seems to be some kind of incompatibility between 9.04 and xVM Virtual Box that did not exist in 8.x for me.

---

### Post by albinootje on 2009-05-08
> **OswaldGlinkmeyer said:**
> When I reboot I get message:[INDENT][FONT=Courier New](EE) Failed to load module "vboxvideo" (module does not exist, 0)[/FONT]
[FONT=Courier New] (EE) No drivers available.[/FONT]
[/INDENT]

Can you uninstall the Guest Additions first and then try installing them again ? Just curious.

---

### Post by OswaldGlinkmeyer on 2009-05-08
> **albinootje said:**
> Can you uninstall the Guest Additions first and then try installing them again ? Just curious.

Uh, I started fresh with a completely new virtual machine in the second case. 

That said, I'd be happy to uninstall them on either one of the virtual machines, but I don't know how to uninstall them.

---

### Post by OswaldGlinkmeyer on 2009-05-22
> **OswaldGlinkmeyer said:**
> Uh, I started fresh with a completely new virtual machine in the second case. 

That said, I'd be happy to uninstall them on either one of the virtual machines, but I don't know how to uninstall them.

I have completely started over with a new install of 9.04 with Vbox, and as soon as I install the Guest Additions, I'm running into the error message.  I found out that even though I used the "Check for Updates" in Vbox, I don't have the newest version, so I'm manually upgrading from 2.1.4 to 2.2.2 to see if that helps.  I'm not sure why the built-in updater in vBox isn't working right.

---

### Post by albinootje on 2009-05-22
> **OswaldGlinkmeyer said:**
> I'm not sure why the built-in updater in vBox isn't working right.

Did you install the OSE or the PUEL version ?

And in case it's the latter, did you use the VirtualBox repositories ? If so, it's won't upgrade 2.0 to 2.1, and won't upgrade 2.1 to 2.2 because the package name is different.
You would install the virtualbox-2.2 from the VB repositories, and that would replace the virtualbox-2.1 package.

---

### Post by OswaldGlinkmeyer on 2009-05-22
> **albinootje said:**
> Did you install the OSE or the PUEL version ?

I used the PUEL version.

> And in case it's the latter, did you use the VirtualBox repositories ? If so, it's won't upgrade 2.0 to 2.1, and won't upgrade 2.1 to 2.2 because the package name is different.
You would install the virtualbox-2.2 from the VB repositories, and that would replace the virtualbox-2.1 package.

OK, I've done that (downloaded and installed 2.2.2).  Now I'm going to create a new virtual machine and attempt to install Xubuntu 9.04 on it and report back.

---

### Post by OswaldGlinkmeyer on 2009-05-22
OK, I was able to solve this by manually installing Vbox 2.2.2, then installing 9.04.  I was never able to get 9.04 to run under 2.1.x.

---

### Post by owenspa on 2009-06-10
I'm running 2.2.4 and came across the same problem when I ran the
version upgrade from a 8.04 (Hardy) virtual machine to 9.04
(Jaunty).  The problem is that GuestAdditions is not installed
after the upgrade. 

The fix is to install it.  Arrange for the ISO file VBoxGuestAdditions.iso
on the host to be connected as the CDROM on the guest, eg using the
"Devices" menu of the virtual machine.

Mount it on the guest

[I]sudo bash
mount /dev/crom /mnt[/I]

Then install GuestAdditions

[I]cd /mnt
sh VBoxLinuxAdditions-x86.run
[/I]
Then reboot the guest as instructed after GuestAdditions is installed.

---

### Post by OswaldGlinkmeyer on 2009-06-12
> **owenspa said:**
> I'm running 2.2.4 and came across the same problem when I ran the
version upgrade from a 8.04 (Hardy) virtual machine to 9.04
(Jaunty).  The problem is that GuestAdditions is not installed
after the upgrade. 

The fix is to install it.  Arrange for the ISO file VBoxGuestAdditions.iso
on the host to be connected as the CDROM on the guest, eg using the
"Devices" menu of the virtual machine.

Mount it on the guest

[I]sudo bash
mount /dev/crom /mnt[/I]

Then install GuestAdditions

[I]cd /mnt
sh VBoxLinuxAdditions-x86.run
[/I]
Then reboot the guest as instructed after GuestAdditions is installed.

That method did not work for me under VBox version 2.1.x.

glink

---

### Post by michael12435 on 2009-07-27
I keep getting the same error, but i did not upgrade, i installed the Vbox Guest Additions on 9.04. so..... i wish they would fix this.

---

