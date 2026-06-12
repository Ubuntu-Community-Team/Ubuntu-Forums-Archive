---
title: "Switching SSD to new pc"
date: 2023-03-10
forum: Hardware
---

### Post by iain_crane on 2023-03-10
Hello,

Running 22.04.2 LTS on a Gigabyte Brix 2807. 

Processor is too slow (Celeron N2807), so planning on upgrading to a Gigabyte Brix GB-BMCE-4500C (Celeron N4500).

These are both barebones machines. 

Can I swap the SSD/RAM from the old to the new? Or...backup, reformat drive, re-install etc. 

Any advice? I contacted the manufacturer, who were unable to provide technical support...

---

### Post by Autodave on 2023-03-10
I generally have no issues when swapping a HD or SSD to a new machine....they just work.  I would make sure that I had backups of all important files that you can't lose!

---

### Post by mIk3_08 on 2023-03-10
> **iain_crane said:**
> 
Can I swap the SSD/RAM from the old to the new? Or...backup, reformat drive, re-install etc. 
 As long as it fit and the connector are suitable to the machine, that's on the go. Regards and cheers

---

### Post by Bashing-om on 2023-03-10
iain_crane; Hello

I recently swapped SSDs into a newer machine - I encountered no issues --- Just works™.
However as Autodave remarks - always good to have that backup insurance.

[INDENT]just turning screws
[/INDENT]

---

### Post by validust on 2023-03-11
Please bear with an amateurs caveat!
When swapping SSD and RAM from one Dell Latitude E7470 (A), to an identical Dell (B), the (B)'s machine id files, in /dev/disk/by-id, was not the same as those in (A)'s /by-id.
As I have SecureBoot enabled, that unabled upgrading shim-signed, grub-efi-amd64-bin and grub-efi-amd64-signed, as well as any thirdparty packages.
My way around it was to copy (A)'s /by-id files and paste them into (B)'s /by-id, and with (B)'s /dev/disk/by-id open, open Synaptic and install those shim-signed, grub-efi-amd64-bin and grub-efi-amd64-signed.

It works, but I wouldn´t mind if one of you kind pros point at the screws I´v missed!

Edit:

Seems the correct way to do it is:

Open BIOS - BIOS Setup - Secure Boot - Expert Key Management - Enable Custom Mode - Reset All Keys

That is if the machine is a Dell Latitude E7470.

---

### Post by iain_crane on 2023-03-18
Thanks for the posts/advice. Will report back when I've got the new box, and tried to switch over SSD/Ram...:o

---

### Post by iain_crane on 2023-06-08
Hello,

Switched from Brix 2807 to Brix GB-BMCE-4500C.

Have made one Bios change as per instruction manual - "USB S55 Wake up Support" now Enabled.

When I boot up I get this message:

>>Checking Media Presence........

And a brief message between iterations:

>>No media present......

Any ideas appreciated.

I have googled this to no avail so far...

---

### Post by oldfred on 2023-06-08
Have you updated UEFI on computer and Firmware on SSD?

---

### Post by iain_crane on 2023-06-08
Hello,

No, have done neither.

UEFI on computer - had a look at support page, BIOS is showing as F5, but F7 is available. Will investigate how to do this..

Firmware on SSD - never updated on old computer. Should I remove from new unit and perform update on old computer then try again?

---

### Post by oldfred on 2023-06-08
My Samsung NVMe drive had a separate bootable ISO. It looked just like an old DOS screen with just an update for my model.
Samsung has a Windows based tool for SSDs, but it does not really work on Ubuntu.

Check with vendor of SSD to see what versions & how to update.

Some new computers can update directly from inside UEFI.
Most require you to download an update file & have it; or extract it into a FAT32 formatted partition as UEFI reads FAT32.
FAT32 partition can be on internal drive or an external flash drive.
Some also have a DOS bootable image to boot & update system.

---

