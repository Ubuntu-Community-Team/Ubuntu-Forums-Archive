---
title: "RH SD card reader on Acer Aspire One ZG5."
date: 2010-02-21
forum: Hardware
---

### Post by stchman on 2010-02-21
Hello all.

I am running Karmic on my AAO.  The LH SD card reader works OOB, but the RH one does not unless I boot up with an SD card.

I have done LOTS of googling and this is the only solution I can find:

Use this command in the /etc/default/grub file.

```
GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1 elevator-noop quiet splash"
```

This does not work.  Anyone have any insight?

Thanks.

---

### Post by stchman on 2010-02-22
No one has any idea?

---

### Post by davec64 on 2010-02-22
It's a common question, unfortunately I'm in the same boat and I've not found a solution either! :)

As an aside, if you want to get suspend & hibernating working you'll need the script here (if you haven't already found it!):

[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10]("https://help.ubuntu.com/community/AspireOne/Ubuntu9.10")

I've also got a ZG5 (A150) and the script works.

I'll keep an eye out and see if someone comes up with a solution re the SD slot. :)

---

### Post by mordalo on 2010-05-05
Wish I could offer advice, but it won't work for me.
I tried a fresh install of 10.04 and it still won't work.

---

### Post by matt-fender on 2010-06-21
This worked for me running Acer Aspire One A150 10.04 LTS

SD cards are working fine but i cannot get XD cards working at all.

---

### Post by scratman on 2010-06-27
The multi card reader on the right side of my Acer Aspire One didn't work at all for me, until I read a workaround that involves having an SD card in at boot time.  The left card reader entitled "Storage Expansion" does not register my SD card at all, and is currently being used as a convenient place to store my spare SD card when it's not in the right hand reader (it sits flush with the case on the left side!!)

Does anybody know how to get the left hand reader working with UNE 10.04?

---

### Post by scratman on 2010-07-01
Happy days, the recent kernel update fixed the issue with the non-working left hand card reader.  Next question, does anybody know how to mount the SD card so that it appears as the Extra Storage it promises to be?  I imagine that it involves something along the lines of a ```
sudo mount dev/sdb/ dev/sda1
``` or something similar, however I'd rather ask if anybody knows how to do it rather than just blunder through hoping for success.

Oh, ideally I'd like this to be a permanent mount performed at boot, as the card's not going to be removed while the netbook is up and running.

Thanks in advance guys, I know you'll deliver.

---

### Post by tonivet on 2010-08-11
I have the same problem with the right card reader on Acer ZG5 but with Memory Stick Pro Duo, it didn't recognise it. Is there any solution?

---

### Post by Hovik on 2010-08-14
My ZG5 (AAO 150) also has this issue. Works fine if the SD card is already in the reader when I boot up though... wish they'd fix that, should be something small I'd think...

---

