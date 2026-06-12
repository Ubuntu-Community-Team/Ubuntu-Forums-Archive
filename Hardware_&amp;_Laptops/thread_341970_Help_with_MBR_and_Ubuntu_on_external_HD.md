---
title: "Help with MBR and Ubuntu on external HD"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by Deived on 2007-01-19
I installed Ubuntu to an external USB HD while booted to the Ubuntu Live CD.  The install went with no problem but now I have a problem when I boot up.

When I attempt to boot without the external HD plugged in, GRUB launches and give me an error (I'm at work so I cant tell when the error is right now, but I can give it later if needed.)  However, when I have the HD connected, GRUB starts up fine and I can choose Ubuntu or WinXP.

My question is, do I need GRUB on my MBR of my main laptop HD in order to boot to Ubuntu? or can I fix the MBR so it boots into WinXP when the drive is not plugged in.  I dont know why the install modified the MBR on the drive that I was NOT installing Ubuntu on and wasn't expecting that.  My laptop has the ability to boot to an external USB drive so I think that's all I need.   So...  can I fix MBR on my laptop and be OK?


ALSO, if anyone can tell me how to fix the MBR on my main drive without booting to a WinXP CD that would be great.  I didn't have much time to look for my disk this morning before I left for work, and would like to fix it on my lunch if I can.

Any help would be much appreciated.

---

### Post by hal10000 on 2007-01-19
the grub config files reside in the partition where you installed ubuntu, so if you plugged off th harddrive grub can't find it's configuration files.

You may fix this if you install the windows boot manager to your permanent harddrive and install grub to the mbr of your usb harddrive drive. But you will need the alterative install cd instead of the usually ubuntu live cd d to do this.

Furthermore you need to do the following things:

1. if your windows uses ntfs as file system then your ubuntu nees the ntfs-3g package: [COLOR="Red"]sudo apt-get install ntfs-3g [/COLOR]

2. copy the existing grub-bootsector to a file: [COLOR="Red"]sudo dd if=/dev/yourusbdrive of=bootsek.lin bs=512 count=1[/COLOR] 
NOTE: /dev/yourusbdrive=the device name of your usb harddrive; i assume that you already installed grub to the mbr of your usbdrive.

3. mount your Windows (system) partition: [COLOR="Red"]sudo mount -t ntfs-3g /dev/hda1 /mnt[/COLOR] (assume /dev/hda1 is your windows system)

4. copy the bootsek.lin file to the root of your windows system: [COLOR="Red"]sudo cp bootsek.lin /mnt[/COLOR]

5. Now boot your windows cd and restore your windows mbr (I guess it's fixmbr or fixboot comand on the windows rescue console) to your permanent harddisk.

6. Boot windows and as Admin open the file C:\boot.ini and change the timeout line to [COLOR="Red"]timeout=10[/COLOR]
and to the end of the file put the following line: [COLOR="Red"]c:\bootsek.lin="Ubuntu Linux"[/COLOR]

NOTE: After a kernel update you don't need to do this procedure again, but if you update your grub to another version then you have to do these steps again.

I hope that's all.

EDIT you don't need the alternative ubuntu cd to install grub bootsector to you usbdrive. You can install it by using the grub command from your existing ubuntu installation.

---

