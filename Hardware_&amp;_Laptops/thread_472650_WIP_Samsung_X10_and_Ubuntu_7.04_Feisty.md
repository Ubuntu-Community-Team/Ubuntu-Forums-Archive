---
title: "WIP: Samsung X10 and Ubuntu 7.04 Feisty"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by drwatson on 2007-06-13
Hi ffffffolks,

currently im trying to get my old and ruined Samsung X10 working with Ubuntu 7.04 Feisty.
I found out the Samsung X10 is the same model as the Gateway 200arc (ppl in the usa dont like to admit that they are buying asian products ;) )

The laptop worked fine with 6.06 and 6.10 afaicr.

The Ubuntu 7.04 CD wont boot, however, complains about not finding the cdrom and drops to a shell.

Luckily my harddrive had to be removed and I tried to install it without the hd attached.

I might (sorry, dont remember) also have tried to pass kernel parameters at the beginning, such as noacpi acpi=off noapm apm=off    and also removed the words "quiet" and "splash".

Eventually i installed the system on a usb stick, which works fine, except for suspend/resume.

Now i found out, that the module ata_piix gets loaded at boot time, which does not find any IDE drives.
If i rmmod ata_piix and modprobe piix things work fine.

What i need to know now is how to correctly disable the ata_piix driver in the kernels initrd.
Since im a linux beginner i have no clue.
I added piix to /etc/modules and i have now created an initrd in which i simply deleted the ata_piix module.

Will keep you informed. Im happy about any additional input regarding the Samsung X10.

---

### Post by drwatson on 2007-06-14
Yup. After my Linux experienced friend lost a few hours over this problem I found the solution:

Once you manage to boot at all

In the terminal enter:

sudo gedit /etc/initramfs-tools/modules

add the line "piix"

save

sudo update-initramfs -u

now make sure that / is mounted by the device /dev/hdaX, not /dev/sdaX

gedit /etc/fstab

The same goes for all other entries with /dev/sdaX
Change them to /dev/hdaX

Also change the line for cdrom from /dev/sr0 or such to /dev/hdc

save and exit

now you may reboot and it should work.


btw this laptop also runs fine when installing ubuntu on a usb stick :-)
Make sure you have a model with low access times. It might give you a speed which is superior to that of an HDD. Certain things, such as suspend/hibernation might not be possible, though.

---

