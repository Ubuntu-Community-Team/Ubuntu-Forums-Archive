---
title: "upgrade motherboard/CPU - any update to GRUB/UEFI?"
date: 2020-05-06
forum: Hardware
---

### Post by yaminb on 2020-05-06
I'm thinking of upgrading my motherboard/CPU. 

Question:
[LIST]
[*]Can I confirm what I need to do  on the software side with respect to Ubuntu. I understand my Windows key might become invalid.
[/LIST]

My main concern is about the boot-loader.
I current have a UEFI setup with a separate EFI boot partitions.
One for my Ubuntu drive.
One for my Windows drive.

It's my understanding that all the boot information is stored on the actual drives, which shouldn't really change.
I'll try to keep the same Sata port numbers. But I don't think it should even matter?

Based on my reading of EFI, if the information is not stored on the firmware (Which it would not be as it's a new motherboard), 
EFI should scan all drive parititions and should be able to find the boot managers in the standard locations, as below.
**However, these are not on the standard name location of '**[B]/EFI/BOOT/bootx64.efi', so it won't be able to find them.

I'll need to boot from a live USB and execute something like:
[/B]sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d /dev/sdX -p NMy understanding is that this should write to the firmware for EFI and add the proper records.
Could I use this for the windows drive (with it's own EFI partition) as well? I 

believe i'd only need to run this command 3 times (BOOT0001, BOOT0002, BOOT 003)

When I'm on the live USB, how do I get all the values for 
[LIST=1]
[*]the drive (/dev/sdX ) I like to make sure all the ids and everything match.
[LIST=1]
[*]In this case you can see BOOT0001 is loading from 1,e76... How do I map this to a /dev/sdX on the live USB. I know this is excessive, but I like to make sure I have all my ducks in a row for such things.
[/LIST]

[*]The partition (N)
[/LIST]

```

sudo efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0002,0003,0004,0005
Boot0001* ubuntu    HD(1,GPT,e76b5eca-5ac7-4da9-a6fd-159f9f2e8c0a,0x800,0x1f4000)/File(\EFI\ubuntu\grubx64.efi)..BO
Boot0002* Windows Boot Manager    HD(3,GPT,d17b2e9b-ff38-435f-962b-e1f90b7d2850,0x209000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)..BO
Boot0003* ubuntu    HD(3,GPT,d17b2e9b-ff38-435f-962b-e1f90b7d2850,0x209000,0x32000)/File(\EFI\ubuntu\grubx64.efi)..BO
Boot0004* Hard Drive     ...
Boot0005* CD/DVD Drive     BBS(CDROM,,0x0).....


```

Thanks,

Yamin

---

### Post by slickymaster on 2020-05-06
*Thread moved to **Hardware**.*

---

