---
title: "Cannot send file to mobile via Bluetooth in Hardy"
date: 2009-06-12
forum: Hardware
---

### Post by mgol on 2009-06-12
Hi,

I've bought USB Bluetooth dongle and I want to use it to contact to my mobile. I'm able to receive files from my mobile, but I cannot send them to it. I tried various things, I installed gnome-bluetooth (it didn't change anything), bluez-gnome, bluez-utils, obexfs, obexftp, gnome-vfs-obexftp etc. I can now browse my mobile using Bluetooth Manager applet (it opens in nautilus a location via obex:// protocol) and I can copy whole folders to my computer, but - again - cannot copy even one file TO a mobile. I keep getting an error:
```
Operation not supported by the backend
```
Any chance of getting my file transfer to a mobile working correctly?

---

### Post by pumatheman on 2009-06-14
Hi, I'm having the same problem with 8.10, my nokia E50, and my Palm LifDrive.

The strange thing is that initially the exploring function was working beautifully on the devicies, I was able to rename, move, erase cut and past all the files I want on my devicies using bluetooth, but not it stops working, its starts giving me the same  error message: 

```
Operation not supported by the backend
```

Now I'm able only to copy stuff from the devicies and the PC I can't do things from the PC to devicies.

In this moment I can send files to the devices only using "send file" function, but this is very uncofortable and limited.

Is there someone who has find a solution? where could be the problem?
upgrading to 9.04 could solve?

---

### Post by mgol on 2009-06-14
See
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/386736](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/386736)
Maybe Your bug is similar? Execute:
```
dmesg
```
and see if Your console is also flooded.

---

### Post by pumatheman on 2009-06-14
thanks for the idea, but: where I can find
```
drivers/bluetooth/hci_usb.c
```  ???

---

### Post by mgol on 2009-06-14
> **pumatheman said:**
> thanks for the idea, but: where I can find
```
drivers/bluetooth/hci_usb.c
```  ???

Errm... It's not THAT simple. This is a file in the kernel sources; You'd have to download them and compile a kernel Yourself. I doubt You want to do that... But I'm not sure if it's going to be fixed in Ubuntu.

---

### Post by pumatheman on 2009-06-14
wow thank's but it's too much for me...
It could be interesting if someone who has the 9.04 could try to see if the bug is still alive in the new ubunto version:D

---

### Post by pumatheman on 2009-06-17
> **pumatheman said:**
> if someone who has the 9.04 could try to see if the bug is still alive in the new ubunto version:D


I've just updated my pc from 8.10 to 9.04, but the problem remains the same :(

---

### Post by Hobgoblin on 2009-06-17
I would suggest a new bluetooth dongle.  Sounds like the one you are using is not well supported under Linux.

I had the issues with mine under 8.04 but it was fixed in 8.10

---

### Post by pumatheman on 2009-06-17
I don't understand... I was having no issues initially with 8.10 but after a while It starts giving me the the errors...
how can I unistall all the bluethooth driver stuff from the pc? 
I' ve tried to disconnect the dongle and riconnect it but the same errors cames out... :(

---

