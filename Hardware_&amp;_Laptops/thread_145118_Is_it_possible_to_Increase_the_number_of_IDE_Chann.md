---
title: "Is it possible to Increase the number of IDE Channels?"
date: 2006-03-15
forum: Hardware &amp; Laptops
---

### Post by maraschin on 2006-03-15
Looks like the problem with missing discs ([http://ubuntuforums.org/showthread.php?t=145070](http://ubuntuforums.org/showthread.php?t=145070)) is some kind of limitation on the number of IDE channels...
Right now I DO HAVE 11 channels but linux will allow (or identify) only 9!

Does any one knows how to change this?
Is it a bug in the kernel or a "feature"?
Why do we have this limitation?

I was planning to add another card and get up to 15 channels...
Yes, 30 discs...

Thanks for any help!

---

### Post by maraschin on 2006-03-18
I manage to find a post with a solution to the problem...
Basicly have to hack in the kernel code...

**Here what I did to enable 12 IDE channels so far:**

Get the kernel source code.

vi /usr/src/linux/include/linux/major.h

add the lines bellow (if you need more IDEs, just add a few more):
#define IDE10_MAJOR 240
#define IDE11_MAJOR 241

vi /usr/src/linux/include/linux/ide.h
Change the number of ports to 12 (or the number you would like to have)

IDE_NR_PORTS (12)

vi /usr/src/linux/drivers/ide/ide.c

Find ide_hwif_to_major[] and add the IDEs you defined in major.h

static const u8 ide_hwif_to_major[] = 
	{ IDE0_MAJOR, IDE1_MAJOR,
	IDE2_MAJOR, IDE3_MAJOR,
	IDE4_MAJOR, IDE5_MAJOR,
	IDE6_MAJOR, IDE7_MAJOR,
	IDE8_MAJOR, IDE9_MAJOR,
	IDE10_MAJOR, IDE11_MAJOR }
..
search for "hwif->name[3] = '0' + index;" and change to the code bellow:
Otherwise you will get some strange names to the IDEs, like ide:  ide;  etc

if (index < 10) {
	hwif->name[3] = '0' + index;
} else {
	hwif->name[3] = '0' + index / 10;
	hwif->name[4] = '0' + index % 10;
}

And finally
vi /usr/src/linux/include/asm-i386/ide.h

changed MAX_HWIFS to the number of channels you would like to have, like 12 for example.

Now just compile the kernel and try it out.
It did work for me, now I've 22 discs dristributed in 12 IDE channels...

---

