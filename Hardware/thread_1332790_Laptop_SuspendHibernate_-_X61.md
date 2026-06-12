---
title: "Laptop Suspend/Hibernate - X61"
date: 2009-11-20
forum: Hardware
---

### Post by jdos2 on 2009-11-20
Used to work well on the IBM X-61, but it's not now on mine- Standard Ubuntu 9.10 install.

Only unusual thing about the laptop- I figure out how to get rotation  with the serial Wacom working.

How does one troubleshoot Hibernation/Suspend issues? Laptop screen goes dark, disks stop working and the poor thing just sits there... Blinking the "moon" icon. Forever.

Nothing in the logs when I have to reboot it - the filesystems are NOT unmounted cleanly, the laptop never goes to sleep- and why doesn't JFS do an fsck.jfs -y to clear the crash flag- why do I still have to do it by hand? Another issue..)

Any ideas?

J

---

### Post by jdos2 on 2009-11-20
And in an unsavory post to myself:

It's the SD card reader- a card in the reader and some bonehead driver somewhere prevents things from working.

Ah, Linux, if it weren't for the caveats... But no, that's what Linux stands for.

---

### Post by miguelito1 on 2009-11-22
> **jdos2 said:**
> Used to work well on the IBM X-61, but it's not now on mine- Standard Ubuntu 9.10 install.

Only unusual thing about the laptop- I figure out how to get rotation  with the serial Wacom working.

How does one troubleshoot Hibernation/Suspend issues? Laptop screen goes dark, disks stop working and the poor thing just sits there... Blinking the "moon" icon. Forever.

Nothing in the logs when I have to reboot it - the filesystems are NOT unmounted cleanly, the laptop never goes to sleep- and why doesn't JFS do an fsck.jfs -y to clear the crash flag- why do I still have to do it by hand? Another issue..)

Any ideas?

J

I have the same problem exactly. I am working for IBM and using the OCDC client of IBM. The ubuntu version is 9.10(karmic). All the updates are completely done. 

However The x61 alway fails to suspend or hibernate. I can not debug the problem either...It prevents me to migrate to ubuntu completely... The moon led blinks forever!

---

### Post by miguelito1 on 2009-11-22
> **jdos2 said:**
> And in an unsavory post to myself:

It's the SD card reader- a card in the reader and some bonehead driver somewhere prevents things from working.

Ah, Linux, if it weren't for the caveats... But no, that's what Linux stands for.

Jdos2,

I don't have any external sd card reader. I don't have an sd card slot on the X61 too. If you mean the PCMCIA slot. I removed the card inside, and it did not help either...:cry:

---

### Post by jdos2 on 2009-11-24
> **miguelito1 said:**
> Jdos2,

I don't have any external sd card reader. I don't have an sd card slot on the X61 too. If you mean the PCMCIA slot. I removed the card inside, and it did not help either...:cry:


Booo! Oh, that sucks. I have an SD reader right above the PCMCIA card- and had a 2GB card in it. Once I ejected it, the laptop started behaving.

But there might be an answer there- is it filesystem related? Do you have any other devices plugged in?

---

### Post by jimmyjones on 2009-11-27
I have the same issue on my Mini 9. If my SD card is mounted the system hangs going into Suspend / hibernate.

I found that all I have to do is un-mount the volume before suspend / resume.

The difference shows up in /var/log/pm-suspend.log.

with the SD mounted I get 'anacron suspend suspend: stop: unknown instance: '

The line is not there with the volume not mounted.

Looks like the SD reader's not being handled properly if it's mounted.

I found a bug report describing this.

edit to add:

This doesn't occur with USB stick file system. 

My SD reader sits on the PCI buss (lspci), the return message from lspci is the same whether or not the card is mounted ?

---

