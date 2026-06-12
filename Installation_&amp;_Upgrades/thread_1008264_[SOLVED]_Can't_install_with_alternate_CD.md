---
title: "[SOLVED] Can't install with alternate CD"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by lardandweed on 2008-12-11
kk, this thread is similar to my other thread found [here]("http://ubuntuforums.org/showthread.php?t=1008015"). (it's a long post) That was addressed specifically for Intrepid and eee PC. However, i found that the problem was more generic as i faced similar issues installing across all my desktops, and even when i tried using Hardy. 

what i'm trying to do is:
install a** CLI ubuntu(any recent revision)** using an **alternate-cd iso** from (not to!) a **usb pendrive** through the components within the **files stored in the usb**. 

It cannot be one installed by downloading components through the network as in eventuality, i want make an install on the eee pc, and the installer does not come natively with the ethernet drivers. Or does anyone have a fix to include the drivers to enable to installer to recognise the network hardware?

Anyway, [COLOR=Red]the problem is that the installer is not able to find the required files on the cdrom[/COLOR]. (i did mount the usb as a cdrom)

Just for the record, here's generally how i prepared my usb stick:
1) partition my usb using fdisk
2) make usb bootable with syslinux
3) Copy contents of iso onto USB stick
              * mount -o loop /path/to/ubuntu.iso /path/to/mount/point
              * cp -r /path/to/mount/point/* /media/disc_label
              4) rename /isolinux to /syslinux and isolinux.cfg to syslinux.cfg


Anyone has any ideas what is wrong? Or can point me to a method which they personally has had success with? (installing with the same configuration)

---

### Post by meindian523 on 2008-12-11
In short,you want to install A only-CLI Ubuntu on your EEEPC through a live install on a USB drive but the installer cannot find the required files on the USB drive,correct?
Could you also post which tutorial you followed please?

---

### Post by lardandweed on 2008-12-11
> **meindian523 said:**
> In short,you want to install A only-CLI Ubuntu on your EEEPC through a **live install** on a USB drive but the installer cannot find the required files on the USB drive,correct?

nope. I install via the pseudo-gui installer. anyway, i thought CLI-only ubuntu is only available in the minimal-cd and alternate-cd? or am i misreading something?

I mainly follow [this guide](https://help.ubuntu.com/community/Installation/FromUSBStick). I've looked around on many other sites that propose quite simliar methods, but its been 3 days and i can't remember which is which. lol

---

### Post by lardandweed on 2008-12-11
Easy - but kinda clumsy - workaround by downloading an intrepid live and loading that onto another USB. then prepared the actual setup USB drive my using the create-usb-tool in intrepid

so... solved! yaay!

---

