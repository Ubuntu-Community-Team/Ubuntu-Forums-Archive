---
title: "usb pen drive - corrupted"
date: 2017-07-11
forum: Hardware
---

### Post by sprinterdriver on 2017-07-11
Hi.

OS: Xubuntu 16.04.2 LTS.
Computer: Dell Lattitude D620

External card reader type HRU-821AL (there is only one slot for SD card on this one)
SD card: Brand: Canon, labeled "SD Memory Card SDC-32M"

So I used this card-reader to move around some small text files between computers (the other one win7 is not supposed to be on same network anyway). The result is broken filesystem (fat).

This is what happens:
- Have used card reader in Xubuntu laptop to just read the contents of a text file, that is very little payload to the SD card.
- Ejected the SD card reader by right click the corresponding desktop icon and selected _Eject_.
- Removed the card reader from Xubuntu laptop.
- Inserted card reader into win7 computer, did some edit - just added one line of text to one text file (seems to work ok at that time)
- Used proper Eject function in windows7 prior to removing usb cardreader from win7 computer.
- Inserted card reader into Xubuntu laptop. Expected icon to appear at desktop, but no icon did appear.
- I then removed the card reader from Xubuntu laptop.
- Rebooted Xubuntu, after logging in to user profile, I inserted the usb card reader yet again. Also this time, no icon did appear on desktop.
- Went back to win7 computer and tried to insert card reader. This time, Windows told me that the drive need to be formatted - e.g. it is corrupted :mad:

This means - somewhere along the way the file system on the sd card has being corrupted, despite I have used Eject in a way that I thaught was apropriate in order to not loose data.

Because this happens I want to ask the following question:

Have I done something that may have lead to the data corruption? Personally I suspect that the when I removed the card reader the first time after the desktop icon did not appear, that is the most probably cause of data loss.

Does the the Eject options in Linux (desktop right-click menu for icon that points to usb volum) works the same way as in windows - from an user's point of view? Could I do something wrong and use Eject and still ending up with a corrupted file system on a usb drive?

When I insert an usb drive and observe that no icon appear on desktop (auto mount?) - What is the correct meassurements to take in order to minimize the chance of data loss?

Does it exist tools for Linux that can restore broken filesystems (FAT) ??


Thanks.

---

### Post by Autodave on 2017-07-11
Your's would not be the first time that I heard of a USB stick, SD card, etc suddenly fail. Did you do something wrong? No. It just happens. I have MANY times just removed a USB stick or card w/o unmounting it first. Accidentally of course, but still have done. And I have never had a problem.

Now, IF you did the unmount or eject command and the PC wasn't done writing to the drive, then you would have caused errors.

For right now, I would try to reformat it and see what happens. If it cannot be reformatted, then you have your answer already: time for a new card/stick.  If it can be reformatted, then I would try copying a few things to and from it before I would trust it.

---

### Post by Autodave on 2017-07-11
You can use *gparted* to try and reformat it. Just make SURE that you chose the right drive!!!!!!!!!!!!!!!!!!!!!

---

### Post by sprinterdriver on 2017-07-11
Thanks for answer.

I just inserted the card reader into the win7 computer avter first having removed the SD card from the card reader and then inserted it again. This time the file system seems to work just fine as if nothing have happens.

I think that the SD card cannot be trusted any more, maybee the card reader too.

---

