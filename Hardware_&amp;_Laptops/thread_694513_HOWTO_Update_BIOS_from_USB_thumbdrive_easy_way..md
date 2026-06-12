---
title: "HOWTO: Update BIOS from USB thumbdrive easy way."
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by SergeiFranco on 2008-02-12
This is my first HOWTO that I would like to share with community.
I was looking every where on how to update BIOS without optical drive, without Floppy or Windows.
I have borrowed a few steps from here [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789) - which is HOWTO flash bios using CD or Floppy (I hope author does not mind).
As far as I know this HOWTO will only work on newer system that recognise thumb drives as USB harddrives.
Please note that my instructions do not involve Windows in any way unlike this [http://ubuntuforums.org/showthread.php?t=484774](http://ubuntuforums.org/showthread.php?t=484774) .

So here are the steps:

**1)** Insert the thumb drive, if the message pops up asking what to do with thumb drive, click do nothing.
You will need to unmount the drive for partitioning and writing MBR, so you will need to issue the following command:
```
sudo umount /dev/sdX
```
Replace X in "sdX" with appropriate letter (mine was sde), which can be found by typing following command
```
fdisk -l
``` 
 Without "sudo" it should only display removable drives, if that does not display anything try issuing "sudo fdisk -l". Alternatively the letter can be found in gparted.

**2)** If you thumb drive is formatted in FAT32, you don't need to follow this step, if it is formatted in other than FAT16 or 32 you will need to format it (**[COLOR="DarkRed"]CAUTION:[/COLOR] formatting obviously leads to data loss on the drive which being formatted**),
for simplicity I used gparted. If you don't have gparted you can install it by typing the following command:
```
sudo apt-get install gparted
```
or if you prefer to use fdisk read the section called "Partitioning Your Disk" in here: [https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)
In gparted I selected my thumb drive in drive selection (it should be on the bottom of the list), and deleted the partition, made new partition formatted it as FAT32.

**3)** To make the thumb drive bootable you will need to get mbr package:
```
sudo apt-get install mbr
```
to write boot sector on the thumb drive I issued the following command 
```
sudo install-mbr --enable A1 --partition 1  --force --timeout 0  /dev/sdX
```
again, replace X with appropriate letter, which can be found using method described in step 1.
This command contains a lot of options, I have introduced them to remove confusing prompt at bootup asking which partition to load from, you can remove all of the switches bar --force.

**4) ** You will need image of a bootable Floppy, I used the same method of obtaining it as described in the HOWTO mentioned above.
The file here [http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz](http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz) contains bootable image of a basic (OEM) Freedos floppy disk, this version does not contain himem.sys so it is suitable for flashing bios. I have extracted it into home directory using Ark but you can use anything you like or just type in command:
```

cd ~
gunzip FDOEM.144.gz
```
(I have put "cd ~" to make sure that your terminal is located in the user's home folder, I also assume that you have saved the file in the home folder).

**5) ** Create new folder in your home folder, either from GUI or by issuing the following command:
```
mkdir fdoem144
```
then mount the image FDOEM.144 into the folder you have created above by issuing following command:
```
sudo mount -o loop FDOEM.144 fdoem144
```
Create a temporary folder to mount the thumbdrive to either from GUI or by issuing the following command:
```
mkdir temp
```
mount the thumb drive:
```
sudo mount /dev/sdX ~/temp
```
again replace X with appropriate letter.

Either copy the files from "fdoem144" folder to the thumb drive using GUI or issue the following 
command:
```
cp fdoem144/* temp/
```

**6) ** Thats it, put your BIOS flasher and ROM file (and whatever files you need) on the thumbdrive.
To clean up do the following steps:
```

sudo sync
sudo umount ~/temp/ 
sudo umount ~/fdoem144/
rmdir ~/fdoem144
rmdir ~/temp

```

After that reboot when you are ready to flash BIOS and select either in BIOS menu (boot disk priority, under Advanced BIOS Options) or by pressing ESC (or what ever it prompts for boot options) after POST to choose from which device to boot (if there is option for that).

Please let me know how this works, and let me know if I forgot something or if I made mistakes.
I hope this is in the right section, if not, mods - please move it to the right one.

Thanks.

Sergei.

---

### Post by mozetti on 2008-02-12
Do I understand you correctly, that once you do this you can restart your computer and boot from the USB memory drive? And from there you run the BIOS flash utility?

Very nifty!

---

### Post by SergeiFranco on 2008-02-12
Yeah, basically you plug in your usb drive and either select it from BIOS to be bootable (Boot Disk Priority), or by pressing "ESC" after POST on many mainboards will give you an option to choose from which device to boot.

---

### Post by wyth on 2008-04-28
Trying this now, and at 
```
sudo mount /dev/sdX ~/temp
```it asks for the filetype.  So I give it the file type, 
```
 sudo mount -t vfat /dev/sdx ~/temp
```and I get 
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
fdisk tells me /dev/sdx is FAT32, so I'm a little stuck.

---

### Post by wyth on 2008-04-28
Nope, just not happening.  No way to get that USB mounted after installing mbr.  Need to find another way to do this because I have a bios update waiting, and some hardware giving me a hard time.

---

### Post by SergeiFranco on 2008-06-06
A stupid question, does it automount?
Also you could try msdos instead of vfat option...
If that does not work try reformating the partition....

---

