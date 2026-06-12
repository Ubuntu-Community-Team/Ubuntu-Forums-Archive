---
title: "Ubuntu doesn't recognise my harddisk"
date: 2010-10-18
forum: Hardware
---

### Post by The_Eggert on 2010-10-18
Hello

Yesterday neither of my conputers would recognize my external harddisk anymore ( I think I screwed up the filesystem or somthing, when I unplugged it while the computer was reading from it..).
But nonetheless, now I just want to format it, so that I can start using it again.. However since it doesn't show up anywhere, how do I format it?
And just for the record, the filesystem was ntfs, and windows can't recognize it either ;)

---

### Post by IcarusR on 2010-10-18
Boot from windows cd & run chkdsk on it.

---

### Post by sikander3786 on 2010-10-18
If you just want to reformat it, please post the output of

```
sudo fdisk -l
```

when it is connected.

It might also be showing up in gparted, it only is not mounting in Ubuntu I guess.

---

### Post by IcarusR on 2010-10-18
> Boot from windows cd & run chkdsk on it.

Maybe able to recover drive if it has been unplugged when using it as op said.

Maybe preferable to try to save data on it before formatting it.

---

### Post by The_Eggert on 2010-10-18
> **IcarusR said:**
> Boot from windows cd & run chkdsk on it.
Didn't think of that ;)
But since Windows doesn't recognize my HDD, will a CD do the trick?
I'll try it nonetheless, and come back with an answer :)

> **sikander3786 said:**
> If you just want to reformat it, please post the output of

```
sudo fdisk -l
```

when it is connected.

It might also be showing up in gparted, it only is not mounting in Ubuntu I guess.

Well that's my main problem :)
"fdisk -l" doesn't show anything but my internal HDD with Ubuntu on it. And neither does Gparted :/
It is as if it isnt even plugged in.

> **IcarusR said:**
> Maybe able to recover drive if it has been unplugged when using it as op said.

Maybe preferable to try to save data on it before formatting it.

The data on the drive isn't that important, since most of it is on my laptop - I just need the drive working ;)

---

### Post by The_Eggert on 2010-10-19
Well I couldn't figure much new out, by trying the Windows cd..

---

### Post by The_Eggert on 2010-10-20
Bump..?
No-one has any ideas?

---

### Post by IcarusR on 2010-10-22
Try unplugging it, wait a few minutes then replug it in & from a terminal run

```
dmesg
```

Check the last 10 or so lines for anything relevant.

---

### Post by The_Eggert on 2010-10-22
> **IcarusR said:**
> Try unplugging it, wait a few minutes then replug it in & from a terminal run

```
dmesg
```

Check the last 10 or so lines for anything relevant.

Thanks for the suggestion - It did give me something, I just don't know what to do with it :P

The output of dmesg:

```


[ 8192.410195] usb 5-2: new full speed USB device using ohci_hcd and address 3
[ 8192.550307] usb 5-2: device descriptor read/64, error -62
[ 8192.811289] usb 5-2: device descriptor read/64, error -62
[ 8193.061313] usb 5-2: new full speed USB device using ohci_hcd and address 4
[ 8193.210335] usb 5-2: device descriptor read/64, error -62
[ 8193.470817] usb 5-2: device descriptor read/64, error -62
[ 8193.761311] usb 5-2: new full speed USB device using ohci_hcd and address 5
[ 8194.181299] usb 5-2: device not accepting address 5, error -62
[ 8194.352560] usb 5-2: new full speed USB device using ohci_hcd and address 6
[ 8194.770706] usb 5-2: device not accepting address 6, error -62
[ 8194.770732] hub 5-0:1.0: unable to enumerate USB device on port 2

```

Does that give you anything?
- Or is there a place where I can read more into debugging this..? :)

---

### Post by sikander3786 on 2010-10-22
Don't know what **IcarusR** comes up after seeing that dmesg log.

What I would recommend after seeing it is to replace the USB cable and see if it mounts now.

---

### Post by The_Eggert on 2010-10-22
> **sikander3786 said:**
> Don't know what **IcarusR** comes up after seeing that dmesg log.

What I would recommend after seeing it is to replace the USB cable and see if it mounts now.

Nope, doesn't do the trick either :)

---

