---
title: "Nokia 6300 phone and USB problem"
date: 2008-10-30
forum: General Help
---

### Post by LianerGoist on 2008-10-30
The Nokia 6300 phone has three connection-modes - Nokia mode, Printing and media, and Data storage. In first mode I can syncronize using OpenSync/Multisync. Second mode kind of works. It automount in Ubuntu 8.10, and I can copy files from and to the card. But there are some strange problems copying mp3 files. I get an error saying something like "error writing file: -108: no such file or directory". I don't get the error copying aac-files or other files. If I use Nokia PC Suite under windows, there are no problems copying mp3-files to and from the phone. 

In this mode (Printing and media) the phone have a strange 'path' - gphoto2://[usb:004,007]/  - well, it works, but looks strange... :-)

In third mode - data storage mode - nothing happens. It tries to connect, but with no luck. This is from system.log:

Oct 30 17:54:11 zepto kernel: [ 9188.052239] usb 4-1: new full speed USB device using uhci_hcd and address 5
Oct 30 17:54:11 zepto kernel: [ 9188.220282] usb 4-1: configuration #1 chosen from 1 choice
Oct 30 17:54:11 zepto kernel: [ 9188.454563] usbcore: registered new interface driver libusual
Oct 30 17:54:11 zepto kernel: [ 9188.483118] Initializing USB Mass Storage driver...
Oct 30 17:54:11 zepto kernel: [ 9188.485125] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 30 17:54:11 zepto kernel: [ 9188.485825] usbcore: registered new interface driver usb-storage
Oct 30 17:54:11 zepto kernel: [ 9188.485834] usb-storage: device found at 5
Oct 30 17:54:11 zepto kernel: [ 9188.485840] usb-storage: waiting for device to settle before scanning
Oct 30 17:54:11 zepto kernel: [ 9188.485854] USB Mass Storage support registered.
Oct 30 17:54:16 zepto kernel: [ 9193.486371] usb-storage: device scan complete
Oct 30 17:54:16 zepto kernel: [ 9193.489187] scsi 4:0:0:0: Direct-Access     Nokia    Nokia 6300       0000 PQ: 0 ANSI: 4
Oct 30 17:54:16 zepto kernel: [ 9193.496118] sd 4:0:0:0: [sdb] 3842049 512-byte hardware sectors (1967 MB)
Oct 30 17:54:16 zepto kernel: [ 9193.499119] sd 4:0:0:0: [sdb] Write Protect is off
Oct 30 17:54:16 zepto kernel: [ 9193.499133] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
Oct 30 17:54:16 zepto kernel: [ 9193.499140] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Oct 30 17:54:17 zepto kernel: [ 9193.517541] sd 4:0:0:0: [sdb] 3842049 512-byte hardware sectors (1967 MB)
Oct 30 17:54:17 zepto kernel: [ 9193.528180] sd 4:0:0:0: [sdb] Write Protect is off
Oct 30 17:54:17 zepto kernel: [ 9193.528195] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
Oct 30 17:54:17 zepto kernel: [ 9193.528201] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Oct 30 17:54:17 zepto kernel: [ 9193.529553]  sdb:
Oct 30 17:54:17 zepto kernel: [ 9193.627420] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Oct 30 17:54:17 zepto kernel: [ 9193.627667] sd 4:0:0:0: Attached scsi generic sg2 type 0
Oct 30 17:54:17 zepto kernel: [ 9193.735235] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Oct 30 17:54:17 zepto kernel: [ 9193.735255] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Oct 30 17:54:17 zepto kernel: [ 9193.742212] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Oct 30 17:54:17 zepto kernel: [ 9193.742230] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Oct 30 17:54:17 zepto kernel: [ 9193.749240] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Oct 30 17:54:17 zepto kernel: [ 9193.749257] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Oct 30 17:54:17 zepto kernel: [ 9193.756198] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Oct 30 17:54:17 zepto kernel: [ 9193.756216] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Oct 30 17:54:17 zepto kernel: [ 9193.763210] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Oct 30 17:54:17 zepto kernel: [ 9193.763229] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Oct 30 17:54:17 zepto kernel: [ 9193.770244] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Oct 30 17:54:17 zepto kernel: [ 9193.770261] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Oct 30 17:54:17 zepto kernel: [ 9193.777186] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Oct 30 17:54:17 zepto kernel: [ 9193.777204] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Oct 30 17:54:17 zepto kernel: [ 9193.784193] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Oct 30 17:54:17 zepto kernel: [ 9193.784211] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information

...and this goes on until I abort the connection on the phone. Could I get this third mode to work? 

Any chance I could get the Printing and media mode to accept mp3 files?

Any help is appreaciated!

Thanks...



Thomas Jensen, Horsens - Denmark

---

### Post by What is in a name? on 2008-10-30
For the record, the storage mode used to work on Hardy Heron. Actually, it's a kernel issue. After upgrading to Intrepid, I kept my old kernel installed aside the new one. If I boot with 2.6.24, my Nokia 6300 connects perfectly. As soon as I'm back to 2.6.27, the issue appears. From what I googled, people at the kernel bugzilla stopped mentioning the issue after 2.6.27-5. But we're on 2.6.27-7 now and the problem remains. Should we open a new bug there?

---

### Post by LianerGoist on 2008-10-31
> **What is in a name? said:**
>  But we're on 2.6.27-7 now and the problem remains. Should we open a new bug there?

Thanks for the info. Yes, will you open the bug report? I don't know the right place to do it, and you seems to know more about it.

-- 
Thomas

---

### Post by What is in a name? on 2008-10-31
> **LianerGoist said:**
> Thanks for the info. Yes, will you open the bug report? I don't know the right place to do it, and you seems to know more about it.

-- 
Thomas

I'm about to go to bed now, but tomorrow (within some hours, anyway) I'll take care of it. I never filed a bug on the kernel bugzilla, but... I'll learn.

---

### Post by What is in a name? on 2008-10-31
So I ended up just adding a new comment to this already existing bug: [http://bugzilla.kernel.org/show_bug.cgi?id=11768](http://bugzilla.kernel.org/show_bug.cgi?id=11768)

I sign as Fábio Barbosa. I'm not aware if there are other means of helping with the issue. If someone wants to help, please let the devs know of the issue, and/or make some suggestions about other solutions.

---

### Post by magnus0 on 2008-11-02
I have a Nokia 6300 too and I'm having the exact same problem.

I could copy .jar files in Printing and Media mode, but not mp3-s.

---

### Post by magnus0 on 2008-11-02
I found there was a patch for it in kernel bugzilla

```
Index: usb-2.6/drivers/usb/storage/unusual_devs.h
===================================================================
--- usb-2.6.orig/drivers/usb/storage/unusual_devs.h
+++ usb-2.6/drivers/usb/storage/unusual_devs.h
@@ -240,7 +240,7 @@ UNUSUAL_DEV(  0x0421, 0x04b9, 0x0551, 0x
                US_FL_FIX_CAPACITY ),

 /* Reported by Richard Nauber <RichardNauber@web.de> */
-UNUSUAL_DEV(  0x0421, 0x04fa, 0x0601, 0x0601,
+UNUSUAL_DEV(  0x0421, 0x04fa, 0x0601, 0x0660,
                "Nokia",
                "6300",
                US_SC_DEVICE, US_PR_DEVICE, NULL,
```

how do I apply it? Can anyone give me command by command instructions?

---

### Post by What is in a name? on 2008-11-02
> **magnus0 said:**
> I found there was a patch for it in kernel bugzilla

```
Index: usb-2.6/drivers/usb/storage/unusual_devs.h
===================================================================
--- usb-2.6.orig/drivers/usb/storage/unusual_devs.h
+++ usb-2.6/drivers/usb/storage/unusual_devs.h
@@ -240,7 +240,7 @@ UNUSUAL_DEV(  0x0421, 0x04b9, 0x0551, 0x
                US_FL_FIX_CAPACITY ),

 /* Reported by Richard Nauber <RichardNauber@web.de> */
-UNUSUAL_DEV(  0x0421, 0x04fa, 0x0601, 0x0601,
+UNUSUAL_DEV(  0x0421, 0x04fa, 0x0601, 0x0660,
                "Nokia",
                "6300",
                US_SC_DEVICE, US_PR_DEVICE, NULL,
```

how do I apply it? Can anyone give me command by command instructions?

I guess you would have to compile the entire kernel, but I'm in no way an expert on that, and it's a risky move if you don't know what you're doing.

---

### Post by DeadEyes on 2008-11-04
I'm having the same problem, guess I'll just have to wait for a kernel update.

---

### Post by szaboistvan007 on 2008-11-09
I have a similar problem. When I choose the data storage function on my phone it keeps saying that data transfer is in progress but nothing happens. The phone's memorycard doesn't get mounted and the processor's load gets higher. After waiting a few minutes I unplug my phone because it seems that nothing is happening. Is this a kernel bug too? It works under windows...

---

### Post by LianerGoist on 2008-11-10
> **szaboistvan007 said:**
> I have a similar problem. When I choose the data storage function on my phone it keeps saying that data transfer is in progress but nothing happens. 

It's the exact same problem. I will wait for the kernel update, unless someone come up with a easy fix.


Thomas Jensen

---

### Post by bryncoles on 2008-11-11
i also get this issue. i can bring files off the phone in print mode but i cant delete or add files.

interestingly, intrepid automatically set me up to use the phone as a modem for mobile internet. 

has anyone tried using 'wammu'? its in the repos and it connects to my phone (select 'nokia mode', then run the set up wizard). 

that might help!

---

### Post by DeadEyes on 2008-11-13
Update to 2.6.27-8-generic doesn't seem to have fixed the problem. I tried wammu and it works in nokia mode for getting info and contacts but what I need is transfering music which I used to do using Rhythmbox.

---

### Post by skiold on 2008-11-15
> **szaboistvan007 said:**
> I have a similar problem. When I choose the data storage function on my phone it keeps saying that data transfer is in progress but nothing happens. The phone's memorycard doesn't get mounted and the processor's load gets higher. After waiting a few minutes I unplug my phone because it seems that nothing is happening. Is this a kernel bug too? It works under windows...

Same trouble here. I have a Nokia 3500c. I can confirm that processor's load gets higher too. I receive same kernel messages like in first post.
I'm subscribed to other thread on the same situation, but no solution yet.
[http://ubuntuforums.org/showthread.php?t=975622](http://ubuntuforums.org/showthread.php?t=975622)

---

### Post by OwnSurname on 2008-11-20
Same here.
I don't really understand how is it possible that it was perfectly working in Hardy Heron, and doesn't in Intrepid. Doesn't make any sense. Let's hope an easy fix will be released soon ...

---

### Post by What is in a name? on 2008-12-02
This workaround worked for me: [http://ubuntuforums.org/showpost.php?p=6231205&postcount=24](http://ubuntuforums.org/showpost.php?p=6231205&postcount=24)

---

### Post by magnus0 on 2008-12-02
> **What is in a name? said:**
> This workaround worked for me: [http://ubuntuforums.org/showpost.php?p=6231205&postcount=24](http://ubuntuforums.org/showpost.php?p=6231205&postcount=24)

It didn't work for me :(

---

### Post by dewert on 2008-12-07
certainly did it for me!

---

### Post by armageddon08 on 2009-01-19
> **dewert said:**
> certainly did it for me!

So is there a solution as of now ?

---

### Post by LianerGoist on 2009-01-20
> **armageddon08 said:**
> So is there a solution as of now ?

Nokia 6300 with firmvare 6.60 has been working some time now, in some kernel versions, but Nokia has just released a new firmvare, version 7.00, so if you use this version, it will not work until one of the next kernel updates. But the guys working on kernel will are aware of the problem and are working on it.

-- 
Thomas Jensen

---

### Post by armageddon08 on 2009-01-20
> **LianerGoist said:**
> Nokia 6300 with firmvare 6.60 has been working some time now, in some kernel versions, but Nokia has just released a new firmvare, version 7.00, so if you use this version, it will not work until one of the next kernel updates. But the guys working on kernel will are aware of the problem and are working on it.

-- 
Thomas Jensen

Okay..Thanks. I really hope they fix this problem asap.

---

### Post by DonkyBoY on 2010-02-21
I am still having issues with this Nokia 6300 and trying to connect to it with Wammu i have tried manual and auto setup but nothing seems to work at all 

so i eneded up here in search of information to find that this has been going on for 3 years (scince the phone was released basicaly)

I am using Ubuntu 9.10 x64 with Wammu 0.30.1-2 (latest version installed thru Synaptic Package Manager)
and Gammu 1.24.0-1ubuntu1

I am using the GNOME desktop

Has any one goten this phone working with this version of Ubuntu ?

all i want to do is backup my phone so if something bad happens i can get straight back to where i was with out the pain of losing all my contacts/calender etc...

---

### Post by NickD-NLUG on 2010-11-13
So... trying to use gnokii or gammu with my Nokia 6300 over bluetooth just results in the software hanging.  It does make some kind of connection as using Ctrl+C to kill the connection brings up an error on the phone.

Anyone else seen the same... and hopefully found a fix?

---

### Post by corbejy on 2011-02-01
Same problem here. Help on this issue would be much appreciated.

Thanks.

---

