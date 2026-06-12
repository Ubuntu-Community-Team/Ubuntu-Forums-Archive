---
title: "How to up USB"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by ShirishAg75 on 2006-08-07
[LEFT]Hi all,
      how do I up the USB? Is there a specific way or is it just plug-n-play. I'm doing this on a friend's laptop hence asking. It's a :-
It's a Compaq Presario M 2253 'AP' or 'AU' don't really know.
        System specs are :-
1.6 Ghz Pentium-M, 40 GB HDD, i915 graphics, 15" display

 Another thing does the USB have to be formatted into ext2,3 partition or can it be save things in FAT32 partition?

 Also what are the ways/apps. one can know CLI as well as GUI that a usb device is there & working properly. 
              Thnx in advance.
[/LEFT]

---

### Post by ShirishAg75 on 2006-08-07
come on guys, somebody plz. tell me something as to what I need to do. Thnx in advance.

---

### Post by TheMono on 2006-08-08
Not quite sure what you mean by Up the USB - it should be plug and play for most devices... What are you plugging in?

I assume from "
Another thing does the USB have to be formatted into ext2,3 partition or can it be save things in FAT32 partition?
"

that it is an external HDD? If so, then any one of those file formats will play nicely, but if it doesn't need to be used by a Windows PC, then use EXT3, otherwise, FAT32.

---

### Post by hil on 2006-08-08
install 'usbview'. launch the program and plug your usb device. If the recognized device in usbview is red, the driver is missing. If you plug a WIndows CE 6.0 device, it'll be red. If you plug a mass storage device, most kernel supports it. At least all ubuntu kernels support it:razz:

---

### Post by ShirishAg75 on 2006-08-09
> **TheMono said:**
> Not quite sure what you mean by Up the USB - it should be plug and play for most devices... What are you plugging in?

I assume from "
Another thing does the USB have to be formatted into ext2,3 partition or can it be save things in FAT32 partition?
"

that it is an external HDD? If so, then any one of those file formats will play nicely, but if it doesn't need to be used by a Windows PC, then use EXT3, otherwise, FAT32.

It's a generic USB thumbdrive. hil would be trying the usbview. Btw was excited to see tht USB thumbdrives are by default activated in Ubuntu. It's also while disconnecting or ejecting tht one either needs usbview or needs to shutdown the computer.

---

