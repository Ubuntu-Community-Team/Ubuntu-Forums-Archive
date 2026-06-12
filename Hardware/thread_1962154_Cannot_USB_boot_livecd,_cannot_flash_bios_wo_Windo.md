---
title: "Cannot USB boot livecd, cannot flash bios w/o Windows"
date: 2012-04-20
forum: Hardware
---

### Post by wkatastrof on 2012-04-20
Hello,

I wanted to try the Fedora 16 live cd on my Acer Aspire 0751h which is currently running only Ubuntu 11.10 with openbox, etc (no unity). Unfortunately, the F16 live cd ruined my Grub...

So I wanted to boot from live usb to re-isntall grub, but my bios usually gives me 'Operating System Not Found.' when I attempt to do that.

This thread here: [ [http://ubuntuforums.org/showthread.php?t=1258634](http://ubuntuforums.org/showthread.php?t=1258634) ] states that they had a similar problem, used windows to flash the bios to the newest version, and then it booted.

The problem is... I have no working OS, let alone Windows to update the BIOS. Acer support was able to give me the .exe files to update the BIOS, but no instructions on how to do so, even for Windows.

Please advise. I'd like to keep using this machine!

---

### Post by MartyBuntu on 2012-04-20
Do NOT flash your BIOS unless it's to remedy a specific problem the manufacturer recommends a BIOS flash for.

You can re-install GRUB by booting to a live 11.10 session.

Option 1:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Option 2:

[http://loewyi.com/info/restoring-grub-ubuntu-11-10/](http://loewyi.com/info/restoring-grub-ubuntu-11-10/)

---

### Post by wkatastrof on 2012-04-20
This is the issue. I can't boot into a Live session via USB because when I attempt to select my Live USB via bios, I get 'Operating System not found.' I think the BIOS flash will fix this according to the thread I linked to.

I have successfully booted this pendrive on other devices. The netbook does not have an optical drive.

---

### Post by MartyBuntu on 2012-04-20
See if you can select bootable devices by tapping F12 at power-on.

---

### Post by wkatastrof on 2012-04-20
> **MartyBuntu said:**
> See if you can select bootable devices by tapping F12 at power-on.


Yes. I have edited my boot options to only include:

USB HDD: Kingston DataTraveler 120 (etc, etc.) -- This is the device with the Live image. 

When I select this, it gives me 'Operating System not found.'

I have booted this pendrive successfully in another machine.

---

### Post by ahallubuntu on 2012-04-20
I have an AO751h.  I'm sure I used Windows to flash the BIOS to latest originally.  I do recall some sort of quick like you describe before that.  Even now, it occasionally won't recognize some boot devices.  I have to turn it on and off a few times.

Did you try resetting BIOS to default settings? I think there's an option in BIOS to do that.  

Are you using the F12 boot menu?  (I think it's F12 - don't have my Acer in front of me.)  You can enable a boot  menu in BIOS though, that I'm sure of.  I'd make sure your USB device is really appearing in the boot menu; it could be not detecting the USB device at all.  If not, try another USB port.  Try physically removing the hard drive once and see if it will detect the USB device then.

Otherwise, you can remove the power, remove the main battery, and pull the CMOS battery (which may be under the keyboard, though - I forget) then hold the power button down for about 30 seconds.  Then re-install the batteries and try it again.  A pain but may work.

FYI, once you get this working, you can install some version of Windows at least long enough to update the BIOS, which might be a good idea.  A generic Windows 7 install disc, for example, will work for 30 days before requiring even a product key to activate it - plenty of time to update the BIOS.  You can grab the correct BIOS files from Acer's website; I'd probably do that myself rather than relying on Acer support to have mailed you the correct files...

---

### Post by oldfred on 2012-04-20
Some BIOS will not boot a device unless it has a boot flag. Grub does not use a boot flag, but Windows has to have one on a primary partition, so those BIOS assume Windows.

Post this to see if you have boot flag.

sudo fdisk -lu

---

### Post by wkatastrof on 2012-04-20
Apparently there is a bug in the BIOS where if Disk-to-Disk transfer is disabled, it cannot boot from CD or USB. I reset those to default, was able to boot into a Debian live session off of USB and have that reinstall GRUB.

Works now.

Hopefully I can avoid having to flash the BIOS or anything in the future.

---

