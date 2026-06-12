---
title: "how to mount a floppy drive?"
date: 2008-08-23
forum: General Help
---

### Post by jlh68 on 2008-08-23
I just wanted a legacy floppy drive on my Ubuntu PC.  I have a lot of old data on floppys (from my windoze days).  I would like to be able to mount my floppy drive and get some of the information from the floppies.

Anyone want to provide me a How-To to set it all up and what to look for, such as the fstab, and other setup stuff.

Thanks.

---

### Post by Butthead on 2008-08-23
It doesn't show up under Storage Media? :confused:

---

### Post by jlh68 on 2008-08-25
No, it does not show.  I thought the first drive was a bad drive and had the manufacturer replace it.  I have made sure that the cables are connected properly.  The access indicator light stays on al the time.

from my /ect/fstab 

/dev/fd0       /media/floppy0  auto    w, user, noauto,exec,utf8 0      0

I hope the above helps in diagnosing and/or figuring out what is happening.

---

### Post by Elfy on 2008-08-25
If the light stays I think there could be a problem with the cable and/or orientation of the plugs.

---

### Post by Butthead on 2008-08-25
I have to agree with ForestPixie (LED staying on usually means cable is plugged in wrong somehow).  You did say you were 100% sure you plugged it in right (shaded cable on pin 1?). :confused:

Maybe try another cable if ones available is the only other suggestion I can offer?

---

### Post by jlh68 on 2008-08-26
Thanks for the input.  Before I tried two different floppy cables, and changed the connections in four different combinations which I think is the maximum for two connectors.  Maybe my motherboard does not communicate to the floppy, I will have to figure out a way to check that.

I will continue to pursue this problem until it is solved.

Thanks to both of you.  Maybe another reader will have some more suggestions?

---

### Post by Elfy on 2008-08-26
You have checked in BIOS I assume? There were a few threads here.

You could see if there are any messages in the log

```
sudo cat /var/log/messages.log|grep floppy
``` - change floppy about fro different words

---

### Post by jlh68 on 2008-08-26
I get the following:
cat: /var/log/messages.log: No such file or directory
john@Eagle:~$ 

What next?

Now let me add a new wrinke to this discussion.  I have rebuild another PC by installing a new MoBo, case fan, and Power Supply and using all the old drives.
I get the same floppy situation with this PC also.  Floppy light stays on all the time.  The unit is an old eMachine with a DVD-RW, CD-ROM, Floppy drive, media card reader, AMD Athlon XP, 2 GB RAM, 120GB HD, D-Link WiFi

With this info, I believe there is something in the Linux OS that has not been configured correctly or something.

---

### Post by jlh68 on 2008-08-26
Old PC does have the floppy drive listed in Places>Computer.  I tried the Format Floppy and the GUI worked, but I did not actually format a floppy.

I also found a file **/etc/fdmount.conf** with a comment that it should only be modified using **/usr/sbin/fdutilsconfig**.

Correction on the install RAM, it is only 1GB on the old PC.

Where do I go next?

---

### Post by Elfy on 2008-08-27
whoops, sorry - pasted wrong one - I haven't either

```
sudo cat /var/log/messages|grep floppy
```

What error do you get if you run this with a floppy in the drive

```
mount /media/floppy0
```

Try this in fstab, in place of the current floppy line - comment out the current one.

```
/dev/fd0        /media/floppy0    vfat    noauto,users    0 0
```

Edit - in addition I would add that maybe you could look into fdmount.

---

