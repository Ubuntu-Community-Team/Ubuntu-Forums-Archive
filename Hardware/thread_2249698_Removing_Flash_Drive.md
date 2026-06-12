---
title: "Removing Flash Drive"
date: 2014-10-24
forum: Hardware
---

### Post by AlexHudghton on 2014-10-24
I use a 32GB flash drive to backup my laptop

When I 'remove safely' the drive has data written to it for between 1 and 2 minutes

Anyone know what it's doing - why is the data not already written?

---

### Post by vasa1 on 2014-10-24
> **AlexHudghton said:**
> I use a 32GB flash drive to backup my laptop

When I 'remove safely' the drive has data written to it for between 1 and 2 minutes

Anyone know what it's doing - why is the data not already written?
You mean the drive's light flashes for quite a while? I see that as well even when I'm unmounting a flash drive which I know hasn't been written to at all. I wonder what goes on when that light flashes. Anyone?

---

### Post by AlexHudghton on 2014-10-24
No, there is a message box which comes up and tells me not to remove the drive until the activity has finished - sometimes I haven't written to the drive either :confused:

---

### Post by pfeiffep on 2014-10-24
> **AlexHudghton said:**
> No, there is a message box which comes up and tells me not to remove the drive until the activity has finished - sometimes I haven't written to the drive either :confused:I've had a similar experience when using Windows 7 - I tracked it down to me having a windows explorer focused on the USB stick. While I'm not suggesting that Ubuntu is equal to Windows but rather the behavior might be. Another possibility is a backup program might be accessing.

---

### Post by tgalati4 on 2014-10-24
If you have any directories open on the flash drive, then it is in use and won't be ejected cleanly.  Understand, that if you are writing a large number of files (as in a backup), it could take several minutes to finish the write.  Don't pull the stick until it is finished, otherwise you will have borked your backup.

---

### Post by Bashing-om on 2014-10-24
AlexHudghton; Hello;

> **AlexHudghton said:**
> I use a 32GB flash drive to backup my laptop

When I 'remove safely' the drive has data written to it for between 1 and 2 minutes

Anyone know what it's doing - why is the data not already written?

If one is writing data to the disk, then that data is 'cached' to enable writing in chunks - faster and better CRC error checking -.
These buffers are not emptied until the drive is 'umounted' .

least ways so
[INDENT][INDENT][INDENT]I have been told, and so I believe
[/INDENT][/INDENT][/INDENT]

---

### Post by AlexHudghton on 2014-10-25
> **Bashing-om said:**
> AlexHudghton;
These buffers are not emptied until the drive is 'umounted' .



Well, that's not right is it? ;) The data would never finish writing to the disk would it?

As to the other replies in the thread - the disk is no longer accessed by any utility - I take it out when I have finished, so the backup utility is gone.

I have taken out a flash drive before the message finished and it does corrupt it, so clearly there is something weird going on here

---

