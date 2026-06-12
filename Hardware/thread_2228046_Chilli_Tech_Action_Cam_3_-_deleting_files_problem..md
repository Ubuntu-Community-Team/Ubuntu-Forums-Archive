---
title: "Chilli Tech Action Cam 3 - deleting files problem."
date: 2014-06-05
forum: Hardware
---

### Post by alexander_smith2 on 2014-06-05
I recently started using a Chilli Tech Action Cam 3 head camera, and I notice an odd problem when using it with Ubuntu 12.10.
I am unable to reproduce the problem under Windows 7. I've not seen any other odd behaviour with other USB gadgets, so I think it is a result of the combination of this camera and Ubuntu.
Like most cameras in its class, the camera only has a USB port for data-transfer and recharging the internal battery. The memory card is removable, but you can leave the memory card in the camera and use the camera as a card-reader.
What seems to be happening is that the free space map map is not being updated after deleting files via the camera. It's a new micro SD memory card.
The problem does not show when using a separate memory card reader. The problem only shows when the memory card is accessed using the camera via USB.
The manufacturer, Chilli Technology has kindly tested the camera for me, and they were unable to reproduce the problem. I think they said they were using Windows XP in-house, but it wasn't Ubuntu. They did say they have seen the same behaviour with Android tablets.

The camera appears as "ID 0472:2053 Chicony Electronics Co., Ltd" according to lsusb. I have captured the relevant part of the message bus, and I will attach it here: [ATTACH]253749[/ATTACH]

Formatting the micro SD card clears the incorrect free space, but that solution seems a lot like using a sledgehammer to crack a nut.

If you need any more information, please let me know. Right now I'm using the camera by removing the memory card every time I want to delete files from it, but I'd like to avoid the extra wear on the micro SD slot.

Alexander Smith.

---

