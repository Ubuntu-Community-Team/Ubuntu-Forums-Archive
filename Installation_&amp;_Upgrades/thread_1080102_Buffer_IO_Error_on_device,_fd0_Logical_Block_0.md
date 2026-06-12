---
title: "Buffer I/O Error on device, fd0 Logical Block 0"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by mongoose_za on 2009-02-25
Morning,

I've currently got Windows Vista Ultra 64bit installed. I wanted to do a dual boot last night with Ubuntu 8.04 Hardy Heron. 
I booted up off the cd and launched the install planning to install Ubuntu on a seperate partition but landing up get this error "[COLOR="Red"]Buffer I/O Error on device, fd0 Logical Block 0[/COLOR]" right after I selected "Install Ubuntu" off the CD.

Originally I thought it's because all the formats of my partitions were in NTFS so I formatted a partition to Ext 3 hoping it would solve the problem but didn't :(

I than ran the cd within Windows and selected "Install within Windows" option and allocated 15GB of space from my primary partition but when my machine rebooted I again received this same error.

Any suggestions?

---

### Post by Partyboi2 on 2009-02-25
Try booting the live cd and when you are at the main menu of the live cd  press F6 and add ```
all_generic_ide
``` to the end of the line as a boot option.

---

### Post by mongoose_za on 2009-02-25
Thanks Partyboi2 I'm going to try that as soon as I get home. I'm running SATA 2 if that changes anything.
5 hours and 45mins until I can go home :/

---

### Post by mongoose_za on 2009-02-25
Partyboi2 you solved it! Thanks. Btw how can I mark this thread as solved?

---

### Post by Partyboi2 on 2009-02-25
> **mongoose_za said:**
> Partyboi2 you solved it! Thanks. Btw how can I mark this thread as solved?
Happy to help. Due to database problems the forums were having awhile ago the option to mark threads as solved has been temporarily disabled. Hopefully it will return soon.

---

### Post by EXCiD3 on 2009-06-04
Ah yes, I forgot about this, must be and AMD motherboard issue. Just built myself a desktop and sure enough, same problem installing LTS as I had before on other AMD desktops, but I had forgotten the boot parameter. Thanks Partyboi2 ;)

---

### Post by cariboo on 2009-06-04
The error you are getting is caused by a non-existent floppy drive. If you disable the floppy drive in the BIOS you won't have the problem again.

---

### Post by EXCiD3 on 2009-06-04
Oh cool, thanks! I never knew what was causing it on the LiveCD, makes sense...should have realized since it says "fd0"...

---

### Post by feardotcom on 2010-06-22
> **cariboo907 said:**
> The error you are getting is caused by a non-existent floppy drive. If you disable the floppy drive in the BIOS you won't have the problem again.

Wow, and to think i was about to start another thread for this exact same problem. Disabled the floppy (in my bios it just gives options for different types of floopies and the first is none) and then 10.4 booted right up, no problems. Thanks.

---

