---
title: "Software to show memory timings?"
date: 2012-10-23
forum: Hardware
---

### Post by Nickolai_Leschov on 2012-10-23
Which software can I use to know frequency and timings of for my memory (RAM)?

---

### Post by IWantFroyo on 2012-10-23
I know Conky can show you how much of your RAM is full. I don't know if it can be configured to show those, however.

---

### Post by wheeze on 2012-10-23
Try this in a terminal:

```
sudo dmidecode -t memory
```

Good info here, [http://www.cyberciti.biz/tips/querying-dumping-bios-from-linux-command-prompt.html](http://www.cyberciti.biz/tips/querying-dumping-bios-from-linux-command-prompt.html)

---

### Post by Nickolai_Leschov on 2012-10-23
> **wheeze said:**
> ```
sudo dmidecode -t memory
```

Thanks. Looks like this could be what I want, but it doesn't show timings for me (I checked all BIOS information pages) and it shows memory type and voltage incorrectly (not that I care about voltage particularly; I know what it is). I'm pretty sure I have DDR3 which should work at 1.5V, it shows DDR2 at 2.9V.

[http://paste.ubuntu.com/1301543/](http://paste.ubuntu.com/1301543/)
btw, how could I paste it here as folded quote?

decode-dimms doesn't work for me either:
```
$ sudo decode-dimms
# decode-dimms version 5733 (2009-06-09 13:13:41 +0200)

Memory Serial Presence Detect Decoder
By Philip Edelbrock, Christian Zuckschwerdt, Burkart Lingner,
Jean Delvare, Trent Piepho and others
No EEPROM found, are you sure the eeprom module is loaded?
```

My computer is ThinkPad X200 with 2GB of DDR3.

---

### Post by Nickolai_Leschov on 2012-10-24
Maybe for now I'll be better off just running memtest86+ for my diagnostic purposes? How do I run it?

I see that I have grub and memtest86+ already installed, but grub doesn't show itself at boot time. It' fine for normal operation, but how do make grub let me select memtest86+ a boot time?

---

