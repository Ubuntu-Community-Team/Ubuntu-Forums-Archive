---
title: "[SOLVED] Camera troubles..."
date: 2008-08-06
forum: General Help
---

### Post by lovhorror on 2008-08-06
I have a Sanyo VPC-S600 digital camera.

When I connect it to the usb it mounts and connects just fine, I can view my pictures and do everything I should be able to. However, if I put in my memory card it not only wont let me view photos, but it won't mount the camera at all.

I'd really like to be able to take more than twelve pictures on my camera, and I'm going on a trip soon so it'd be nice if I could view my pictures on my computer when I get home.

I really need help with this one, thanks in advance for any responses.

---

### Post by Brunellus on 2008-08-06
I am moving this to an appropriate support forum.

---

### Post by red_Marvin on 2008-08-06
Do you mean that you can't view the contents on the memory card when put in a memory card reader, but can read them when using the camera as a reader? Please clarify.

---

### Post by lovhorror on 2008-08-06
I don't know what you mean.

If I connect the camera without the card in everything goes fine.

If the card is in it wont mount at all. Although, before, it used to still recognise the camera with the card in, but I couldn't view the contents.

I don't know how to be more clear.

---

### Post by red_Marvin on 2008-08-07
It was I who misunderstood.

I've been unable to find any useful info on google on this problem, so I'd suggest getting a external memory card reader to get the files.

When I check what cameras are supported by gphoto2 (*gphoto2 --list-cameras* [SIZE="1"](gphoto2 is based on libgphoto2 which is what I think is used to communicate with cameras)[/SIZE])
there are some sanyo cameras there, but not your model, sorry.:(

---

### Post by lovhorror on 2008-08-07
There's gotta be some other way to see my pictures, dammit. I thought ubuntu was supposed to be able to do everything except video games (and I can even do that!). There must be some way for me to see these things.

---

### Post by cariboo on 2008-08-07
Post the output of dmesg when you plug your camera with the memory card in. In a terminal:

```
dmesg
``` 

The last 20 lines are all that is needed.

Jim

---

### Post by lovhorror on 2008-08-07
I estimated 20 :3

> [ 5679.392896] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 5679.392902] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
[ 5679.392907] end_request: I/O error, dev sdb, sector 227
[ 5679.401896] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 5679.401904] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
[ 5679.401911] end_request: I/O error, dev sdb, sector 0
[ 5679.408915] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 5679.408923] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
[ 5679.408932] end_request: I/O error, dev sdb, sector 8
[ 5679.415885] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 5679.415891] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
[ 5679.415897] end_request: I/O error, dev sdb, sector 0
[ 5679.422907] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 5679.422917] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
[ 5679.422926] end_request: I/O error, dev sdb, sector 0
[ 5681.797579] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 5681.797587] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
[ 5681.797593] end_request: I/O error, dev sdb, sector 0
[ 5681.804576] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 5681.804584] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
[ 5681.804590] end_request: I/O error, dev sdb, sector 0
[ 5681.811567] sd 4:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 5681.811573] sd 4:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
[ 5681.811578] end_request: I/O error, dev sdb, sector 0
[ 5763.978821] usb 4-2: USB disconnect, address 2
[ 7712.653191] usb 4-2: new full speed USB device using uhci_hcd and address 3
[ 7712.830265] usb 4-2: configuration #1 chosen from 1 choice
[ 7712.834329] scsi5 : SCSI emulation for USB Mass Storage devices
[ 7712.834490] usb-storage: device found at 3
[ 7712.834494] usb-storage: waiting for device to settle before scanning


---

### Post by lovhorror on 2008-08-09
bump

---

### Post by lisati on 2008-08-09
There might be some setting in your camera somewhere that needs to be checked.

When I connect my HDD camcorder to my computer (either Windows or Ubuntu), I have to actually tell it to use its HDD or its memory card - if I forget to do so, the computer won't recognize it.

My digital stills camera has a setting that lets me choose either the internal memory, the SD card, or both.

---

### Post by lovhorror on 2008-08-09
I just checked and I can see the usb device in the computer folder, but it says it can't mount the file. When I go to properties it doesn't have anything listed for any of it. It just seems to be that the computer is failing to recognise what is connected to it. It feels like there's an easy fix here that nobody is seeing.

---

### Post by lovhorror on 2008-08-10
bump for desperation...

should i just buy a memory card reader?

---

### Post by lovhorror on 2008-08-14
15$ sandisk memory card reader did the trick.

---

