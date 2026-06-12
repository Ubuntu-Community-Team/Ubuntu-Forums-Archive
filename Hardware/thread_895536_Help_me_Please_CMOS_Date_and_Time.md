---
title: "Help me Please CMOS Date and Time"
date: 2008-08-20
forum: Hardware
---

### Post by macnyak on 2008-08-20
Please Help me, This is what my PC always displays when i turn it on:




Phoenix-Award BIOS v6.00PG, An Energy Star Ally
Copyright (c) 1984-2005, Phoenix Technologies, LTD
U8668R35-D

Main Processor: Intel (R) Celeron (R) CPU 2.26GHz (133x17.0)
Memory Testing: 524288K OK
Memory SPD is DDR333

Primary Master: ST320410A 3.39
Primary Slave: Hitachi HDP725025GLAT80 GM20A42A
Secondary Master: HL-DT-STDVD-ROM GDR81648 OM2O
Secondary Slave: None

Primary IDE Channel no 80 conductor cable installed

Floppy disk(s) fail (40)
CMOS checksum error-Defaults loaded
Warning! CPU has changed or CPU Ratio changed fail
Please re-enter CPU settings in the CMOS setup and remember to save before quit!

Press F8 to enable System Configuration
Press F9 to select Booting Device after POST
Press F1 to continue, Del to enter Setup

03/23/2005/P4M266A-8235/7-6A6LWOOHC-OO 




Questions:
1. what does this mean:   "Primary IDE Channel no 80 conductor cable installed"?

2. why does this messages appear? i don't have any floppy disk drives in my PC

3. how can i fix: "CMOS checksum error-Defaults loaded
Warning! CPU has changed or CPU Ratio changed fail
Please re-enter CPU settings in the CMOS setup and remember to save before quit!"

4. i already replaced the CMOS battery but this things always appear, and even if i change and save things up in the CMOS like my Hard Drive to be the 1st boot device, when i turn off the PC nothings been saved.

5. please help me to fix things, and every time i press F1 or let the computer boot into windows the date is January 1, 2005.

6. how can i prevent this message from appearing? i want my PC to boot directly on my 1st hard drive.

7. why does the BIOS don't accept the changes i made even if i save it?

please help me step by step to fix it and or links on updating the BIOS of my PC. please help me. i really will appreciate all your help. thanks and GOD bless...

---

### Post by Thingymebob on 2008-08-20
Get hold of the manual for your mainboard, If you have replaced the cmos battery this looks as if you have a bios reset jumper in place. The manufacturers website is probably the best place to start.

---

### Post by prshah on 2008-08-20
> **macnyak said:**
> 
Primary IDE Channel no 80 conductor cable installed It means that you are using a 40 channel cable instead of an 80 channel cable; essentially, the ribbon cable connecting you hard disk to the motherboard is an inferior one. A proper 80 channel cable will be a little stiffer than a 40 channel cable and will give much better performance. (Better IO shielding, better performance, lesser errors), but it has to be installed in a particular way.

> **macnyak said:**
> 
Floppy disk(s) fail (40)
CMOS checksum error-Defaults loaded

Your CMOS battery on the motherboard needs to be changed; It is usually a CR2032 3v "coin" battery.

> **macnyak said:**
> 
Warning! CPU has changed or CPU Ratio changed fail
Please re-enter CPU settings in the CMOS setup and remember to save before quit!

After changing the battery, and finishing the CMOS setup, and saving it, you will not get any such messages in the future.

> **macnyak said:**
> 
4. i already replaced the CMOS battery but this things always appear, and even if i change and save things up in the CMOS like my Hard Drive to be the 1st boot device, when i turn off the PC nothings been saved. Either the CMOS battery you've replaced is faulty, or you've left the CMOS memory jumper in the wrong setting.

---

### Post by macnyak on 2008-08-20
i don't have the manuals or driver of this motherboard because i am  not the  original buyer of this PC, but after days of search in the internet and taking a very good look at the motherboard i found out that this is my motherboard,

please click on the link:

[http://www.biostar.com.tw/app/en-us/mb/content.php?S_ID=242](http://www.biostar.com.tw/app/en-us/mb/content.php?S_ID=242)

---

### Post by prshah on 2008-08-20
> **macnyak said:**
> i found out that this is my motherboard,


As per this motherboards manual you will find a jumper set titled JCMOS near the battery (CR2032 3v "coin" battery). The "jumper set" will be a set of 3 tiny rods, and at one end, it will be marked "1" (numeral one). It will be at the edge of the board, between the battery and the IDE ports.

For normal CMOS setup: Short pins 1-2 (Eg, the little plastic piece must cover pins 1 and 2).

To clear CMOS memory: Short pins 2-3 (Eg., the little plastic piece must cover pins 2 and 3).

Now, if in fact your battery is OK, then there are 4 possibilities:

1) Your "plastic piece" (techtalk: jumper) is shorting 2-3, not 1-2. Change it to short 1 & 2, boot, setup CMOS and save, and you should have no further problems. Also note that if this is the case, your (new) battery might have probably drained by now, so it will be a good move to replace the battery as well.

2) The jumper is totally missing. In that case, get a jumper (you can pull it off the back of an unused old CDdrive and/or hard disk drive) and short 1-2 as mentioned above. All advice as per the previous point also applies here.

3) The jumper is there, and in the correct place, but faulty. Replace the jumper and follow all advice from point 1.

4) The motherboard itself is faulty, or there is a short somewhere. Remove the board, clean it both sides using a soft brush, and try again.

Post back if you need more details on any point.

---

