---
title: "Western digital external HDD"
date: 2011-03-19
forum: Hardware
---

### Post by mgmyers on 2011-03-19
I've got my new HDD formatted in ext3 using Gparted and figured out how to mount it (basically plug in the USB after computer has started).  My trouble is permissions.  I am logged in as root, far as I can tell from the users and groups box in administration, but it denies my attempts to put folders onto the external HDD saying I am not the owner.  

Is there some way I can make it always accessible to me?  I basically want to use it as an extension of my file system.  It would also be neat if I could load an iso of 10.4 on to it for trial purposes, as I am running 8.04 now.  Would I need a partition for that?

---

### Post by varunendra on 2011-03-20
Try unmounting it manually, then remounting as root. Then you can set its permissions to be accessible for everyone. (you can try gksu nautilus command to set permissions using GUI)

To unmount, you can simply click the "eject" button showing against that drive in nautilus. To remount as root, you may have to use commandline. For example:
```
mkdir /mnt/drv1
sudo mount /dev/sdb1 /mnt/drv1
```
(assuming you are not already root, and sdb1 is your external drive that you want to mount in /mnt/drv1 directory)

[Note: $ sign in terminal prompt shows you are in user mode, while # sign shows you are already root]

To make it always accessible (if changing permissions doesn't solve the problem), you may have to make an entry for it in fstab which I'm not sure how to do correctly.


As for installing 10.4 on it, booting from live (or alternate) CD should automatically allow this without any trouble. However, if you opt for that, and your computer has the capability to boot from USB drives, it'll be a good idea to install GRUB (using "advanced" mode) on the external drive itself rather than installing it on the internal drive.

Again it is also a good idea to create a separate small partition (6-20GB) for this kind of installation, and let the remaining space be freely shared by both installations. But it is not necessary.

---

### Post by vanadium on 2011-03-20
> **mgmyers said:**
> I am logged in as root, far as I can tell from the users and groups box in administration, but it denies my attempts to put folders onto the external HDD saying I am not the owner. 
You should NEVER be logged in as root. As a matter of fact, in a default Ubuntu install, you can't.

This is Linux, so you should know about owners and permissions. By default, a linux system is secure. You can only write within your own home directory. In order to have write permissions elsewhere, you need to be granted these. Permissions are granted by a user with root privileges.

A graphical way to act as root in order to change permissions is to open nautilus with root privileges. This is done through the command "gksudo nautilus". With the nautilus instance that appears, navigate to where you want to obtain write permissions. Right-click, properties, permissions tab: change the user.

[quote=varunendra]
Try unmounting it manually, then remounting as root. [/quote]
This is not needed. As you observe yourself, an external drive is automatically mounted. Why would you mount manually?

[quote=mgmyers]Is there some way I can make it always accessible to me? I basically want to use it as an extension of my file system. It would also be neat if I could load an iso of 10.4 on to it for trial purposes, as I am running 8.04 now. Would I need a partition for that?[/quote]
In this case, you will need to mount the removable drive by adding a line in /etc/fstab, and as such override the automatic mounting mechanism. That way, it will be available automatically during startup. Such a setup is designed for static drives, so it would assume that your external drive is always connected and turned on.

"Loading an iso for trial purposes" involves quite a heavy change to your system. Indeed, you could attempt what varunendra suggests and install Ubuntu 10.4 and grub onto your external drive. This is at your own risk, though. Installing an OS on an USB drive is not the best thing to do.

A more robust approach would be to create a 10 GB partition on your internal drive for installing experimental operating systems. That installation will be able to use the same swap partition as your main OS. You can store your data on the other media.

---

### Post by varunendra on 2011-03-20
> **vanadium said:**
> You should NEVER be logged in as root. As a matter of fact, in a default Ubuntu install, you can't.
+1

> **vanadium said:**
> This is not needed. As you observe yourself, an external drive is automatically mounted. Why would you mount manually?
..because I was having similar problem with one of my external drives (NTFS) a couple of days ago, and I found this solution in some post (which I've lost track of) that worked instantly.
Whatever the original solution provider explained to be the reason implied that in fact the "automount" feature itself causes this trouble sometimes by using some weird permission profile (that won't let even root to change permissions!) while "automounting" an external drive. So remounting it manually as root allows to make changes as required.

> **vanadium said:**
> A more robust approach would be to create a 10 GB partition on your internal drive for installing experimental operating systems. That installation will be able to use the same swap partition as your main OS. You can store your data on the other media.
+1

---

### Post by vanadium on 2011-03-20
> **varunendra said:**
> +1
..because I was having similar problem with one of my external drives (NTFS)...
With ntfs drives, it is a problem indeed. Permissions of ntfs drives cannot be changed after mounting (even not the mount point). Drives are mounted with permissions for the current user. If the next user logs in, he cannot use not unmount and remount the drive safely. I even had rumours that the ntfs drive gets mounted with permissions for root when it is attached on the system during startup.

Previous Ubuntu versions would mount ntfs drives with all permissions open. I think this was the best approach from a practical viewpoint. The current approach is better in terms of safety, but can be a major frustration.

Anyway, back ontopic ;)

This here concerns an ext4 drive, and in that case, there are no issues at all with permissions. You can granularly set permissions on the directory and file level as with any file system that supports unix permissions.

---

### Post by mgmyers on 2011-03-20
Thanks a bunch.  The gksudo nautilus worked at getting me permissions, and I have been able to clear nearly 8 gigs of internal hd space with the copying.  I can see why linux is so damn secure now!:)

I have a really small internal hd, not enough room even now for a 10 gig partition, which is why I was thinking of using the external for trial.  I'll make further attempts to get this external cd drive to work (usb) in order to burn the iso.  Does it make a difference that it is connected via usb?  

I'll have to give it a couple of days before knowing whether the fstab entry will be necessary.  It sounds mysterious.  Since I have loaded 8.04 via a thumb drive before, or at least attempted to, my bios is set to scan usb on startup.  I'm unsure still how this auto mounting works, but all is pleasant for the moment!

---

### Post by varunendra on 2011-03-20
> **vanadium said:**
> With ntfs drives, it is a problem indeed. ..............  that supports unix permissions.
Nice explanation! Thanks for it! :)

> **mgmyers said:**
>  I'll make further attempts to get this external cd drive to work (usb) in order to burn the iso.  Does it make a difference that it is connected via usb?
No, it won't make much difference as long as ubuntu is able to detect it as a cd writer and can use it in USB2 mode. However, if your computer only has USB1 or 1.1 (I assume by your system's description you've provided so far), then data transfer speed may be a problem (11-12 Mbps at most).

you can confirm the USB mode in use by:
```
lspci | grep HCI
```
Regardless of the available speeds, it is always recommended to write optical disks with the minimum available speed not only to avoid buffer underrun, but also to ensure good quality of writing.

However, I believe there is another way (I haven't tried it though, and is not recommended if your USB drive contains important data) that should do just fine to install Ubuntu on a USB drive without a physical CD. I'd try it as follows:

[LIST=1]
[*]Install Virtualbox PUEL (not OSE, since it doesn't have USB support) on current Ubuntu setup.
[*]Create a virtual machine for Ubuntu with no hard-drive.
[*]Connect the external hard drive to this virtual machine as the only available hard drive and install Ubuntu on it using iso image of installation CD.
[*]Shut down the virtual machine and restart computer booting off this external drive this time to get the fresh installation configured as per the real hardware.
[/LIST]
But as I said, this is just an idea which I haven't tried myself. If you wish to try this, make sure there is no such important data on the external drive that you may have to regret loosing!

---

### Post by mgmyers on 2011-03-20
varunendra, I ran the command you gave: 
lspci | grep HCI
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)

Does this mean I have three usb1 ports and one usb2?  How would I know which is which?  I'm so happy to be downloading straight to my external now!

I have zero experience or knowledge of virtualbox and need to do some reading before playing around with it.  Thanks for the suggestion though.  I've been trying to get a lot of the old rpg games to work in linux and several apparently only can using this virtualbox.  I'm still fiddling with the dosbox though!  Just today started thinking about the psx emulators available...

---

### Post by varunendra on 2011-03-21
Good to hear you're happy!
> **mgmyers said:**
> Does this mean I have three usb1 ports and one usb2?  How would I know which is which?
Theoretically Yes, and this is normal. :)
for more info on USB terminology vs functionality : [http://en.wikipedia.org/wiki/Host_controller_interface](http://en.wikipedia.org/wiki/Host_controller_interface)

As for detecting the correct port for USB2, I'm not sure if this is required at all. I think it is possible for manufacturers (perhaps even common) to dedicate one high speed controller to all four ports such that any of them would do the job in high speed. (this may be the explanation why you see 4+1 controllers but only four ports)

Well, in order to make sure a device is connected in USB2 mode, you may follow this:

Just connect a USB drive, let it be detected, then type in the following command in terminal:
```
dmesg | tail -20 | grep USB
```if you see lines saying "....high speed.... using EHCI...." it means you are good to go!

However, do consider tips like using short-size cable, preferably backside (onboard) ports, etc. to ensure good quality of signals.

For more info on USB testings, tips & basic troubleshootings:
[http://www.linux-usb.org/FAQ.html](http://www.linux-usb.org/FAQ.html)
[http://www.linux-usb.org/usbtest/](http://www.linux-usb.org/usbtest/)

For installing virtualbox (not virtualbox-ose), this may help:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
(download deb package, add repository,.... whatever suits you)



**_PS_:**

This thread may be of great help for virtualization related FAQs: [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

**_PS2_:**

Demo for creating and using a virtual machine in VirtualBox: [http://ubuntuforums.org/showthread.php?t=1711228](http://ubuntuforums.org/showthread.php?t=1711228)

---

