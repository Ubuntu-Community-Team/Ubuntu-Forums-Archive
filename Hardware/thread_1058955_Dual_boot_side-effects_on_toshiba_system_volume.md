---
title: "Dual boot side-effects on toshiba system volume"
date: 2009-02-03
forum: Hardware
---

### Post by Sidneyaks on 2009-02-03
Ok, so first off from what I've read most Toshiba laptops come with a "Toshiba System Volume" hidden from vista which is more or less a recovery partition so you don't really -need- the disk.

Unfortunatly, that means I didn't GET a disk! Sparing you my thoughts on such a flimsy recovery method, I'd like to ask a few questions.

1.) Now that I know that it's there (thanks Ubuntu) is there anyway I can simply copy the entire partition over to a DVD so that I have a disk I can boot from? If so would formatting that partition and adding it to one of my others be possible?

2.) If the above is not possible, how can I add booting from that partition to Grub? Would it be possible to password protect it?

For the record, there's nothing wrong with either of my Vista or my Ubuntu partition, but I only barely have an idea of what I'm doing in the terminal and would like to know for sure that I am able to restore my computer if I screw it up.:p Thanks in advance.

---

### Post by shadowhacker on 2009-02-03
> 1.) Now that I know that it's there (thanks Ubuntu) is there anyway I can simply copy the entire partition over to a DVD so that I have a disk I can boot from? If so would formatting that partition and adding it to one of my others be possible?

Maybe. Mine is too big to fit on even a a DL DVD (9.5GB.) Even if yours will fit on a DVD, I will tell you right now this method is a royal PITA, because they set up the recovery partition knowing that it is on a Hard Drive, and therefor it has write access for logs and what-not (can't write to a disc.) The easier method for this is using a USB flash drive with enough space for the partition, then it is just a matter of formatting it with windows and making it bootable, then booting from linux and copying every single file over. You may run into a few problems even here though, because Micro$oft engineers and PC manufacturers are notorious for using hard paths instead of system variable paths. (I.E. "D:\" instead of "%cdrom1%\".) Due to this, even with the USB method; editing of some config files may be required.

> 2.) If the above is not possible, how can I add booting from that partition to Grub? Would it be possible to password protect it?

This is the method I would recommend, because it is WAY easier; especially if you're not comfortable messing with the above option. This is simply a matter of editing your menu.lst file for grub.

```
sudo gedit /boot/grub/menu.lst
```

You'll want to add something like this to the very bottom of the file:

```
title		Microsoft Windows Vista Home Premium x86 (Recovery)
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```

Replace (hd0,2) with the location of your recovery partition. You can find this using gparted. (Remember to subtract 1 from the number gparted gives you. I.E. /dev/sda3 = hd0,2)

For password protection; add the following code to the top of menu.lst:

```
password yourpasswordgoeshere
```

Then, add this command under your vista recovery boot option:

```
lock
```

The finished product should look something like this:

```
title		Microsoft Windows Vista Home Premium x86 (Recovery)
root		(hd0,2)
savedefault
makeactive
chainloader	+1
lock
```

---

### Post by shadowhacker on 2009-02-03
Another option is what I did:

I called up HP support and told them that I got a massive power spike which toasted my Hard Drive. I told them it still worked fine, but all of the data was corrupted, and asked if they could send me a recovery DVD for my laptop. They did, and I freed up 10GB of hard disk space. Mine was under warranty still, but I don't know if this is necessary. Either way; it never hurts to ask.

---

### Post by Sidneyaks on 2009-02-03
:P I'd thought of that. I just think that it's so much BS that they can't even just tack an extra $10 on so that I can have a hard copy of my factory settings. I paid for the liscense for windows vista when I bought the thing, why don't they give me a cd to go with it?

Anyway, yeah, I think I might give them a call some time. Thanks for your help with the boot records again.

---

### Post by shadowhacker on 2009-02-03
> **Sidneyaks said:**
> :P I'd thought of that. I just think that it's so much BS that they can't even just tack an extra $10 on so that I can have a hard copy of my factory settings. I paid for the liscense for windows vista when I bought the thing, why don't they give me a cd to go with it?

Anyway, yeah, I think I might give them a call some time. Thanks for your help with the boot records again.

I completely agree. Anything to save a buck, I guess.

No problem on the code. This forum has helped me through multitudes of issues, I felt the least I could do was give something back.

---

