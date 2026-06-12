---
title: "Mounting Problems - Karmic"
date: 2009-12-16
forum: Hardware
---

### Post by nicknefarious on 2009-12-16
I am having some issues with mounting on my Karmic install. I have two drives - a 500GB Samsung internal, and a 320GB Samsung internal mounted in an external USB enclosure. My goal is to have them both setup and run a backup/sync of both OS and data once a week to the external 320GB so if my internal HDD ever dies I can just pull the internal one out and slide the spare one in and away I go.

Mount problems - When my install boots without any USB installed, my places menu shows two links for each partition (there are 4 partitions) of the internal drive. One of each of the links works, and one gives an error saying the partition is already mounted (which is true - I have them mounted at boot - through fstab). Why are these extra entries in the Places menu? They appear in the Nautilus navigation bar as well? Some show as mounted and some show as unmounted for the same partition. I want to correct whatever the underlying problem is, not just make them disappear. 

When I plug my USB external HDD in everything changes and the places menu becomes a bigger mess. This is different depending on whether the USB is plugged in during boot or if I wait until the boot has completed. Under the 'Removable Drives' menu of the dropdown 'Places' menu there are three entries for each of the internal partitions and two for each of the USB connected external partitions. Again, why? How do I fix this properly - not just make the icons disappear.

I have cloned my OS from the the boot partition of the internal drive to the same partition of the external drive but when I plug the external drive in through USB the three other partitions automount like normal but the OS Bootable partition does not. When I open gParted it shows and says their is an error about the mount point for this partition. It shows the partition as being mounted, but I can't find it anywhere. It does not appear in mtab. When I try to unmount it through gParted it won't allow me. I need it to be mounted properly so I can sync OS changes across to it.

I have seen similar problems throughout the forums but can't find any real fixes, just options to make them disappear - doesn't solve my functionality problems.

Any help is greatly appreciated - as too are any detailed explanations about underlying causes and reasons for the problems and terminal commands - so I can learn for myself.

What I really want to learn here is what controls what is automounted and what is not? How does the placement of your mount point folders inside or outside of the home folder affect how or where they appear "automagically"? Or it doesn't. Where does Nautilus and the places menu extract it's information about mounted and removable devices from?

I have attached my fstab and mtab (with usb external plugged in)

Thanks greatly,

Nick

---

### Post by oldfred on 2009-12-16
When you cloned the drive did it keep the same UUIDs? The system usually does not boot with duplicate UUIDs or may be why you have the issues you are having.

run ( I am never sure if sudo is required)

blkid

or 

ls -l /dev/disk/by-uuid

---

### Post by nicknefarious on 2009-12-17
I checked using ```
sudo blkid
``` and you are correct. The UUID has been duplicated/cloned across to the boot partition of the external USB drive. How can I edit the UUID of the boot partition of the external drive? Is this the correct solution? It says it is mounted, but it is not.

This is one part of the problem. This does not effect the multiple entries of the same partitions in the "Places" and Nautilus menus.

Thanks,

Nick

---

### Post by oldfred on 2009-12-17
If you want a true clone you do not want to edit the UUID. Internal files like grub, fstab and maybe others use the UUIDs so you cannot change them and have a working clone. Backup would be better if you want a working second drive.

---

