---
title: "My computer have problems each morning &quot;at cold&quot;."
date: 2013-10-03
forum: Hardware
---

### Post by utilisateursys on 2013-10-03
Every morning I turn on my computer and ... 

_ Case 1: _
Immediately if I start on the hard drive with Ubuntu installed, it hangs or is unstable. 

_ Case 2:  _
Immediately if I run a Ubuntu Live USB, it always crashes with a message like the following: 
[x.xxxxxx] kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0) 

_ Case 3: _
Immediately if I run an Ubuntu Live USB and memtest86, he finds many errors (using only one memory module it finds no errors). 

Turning on my computer a few minutes after the first test, I do not have any of these problems. 
"To Hot" Ubuntu works perfectly : IPDT, systester Pro V1.6.0 and memtest86 find no errors.
    [U]
My computer :[/U]
Motherboard with Intel H61
    Processor Dual Core 
    Memory 2 x 1 Go       PC10600 
        Disk drive S-ATA -       500 Go - 16 Mo 

I don't know what is the part in default ?

---

### Post by utilisateursys on 2013-12-01
Good evening.

I changed the motherboard with a new one, different brand, with an Intel H61 chipset.

---

### Post by utilisateursys on 2014-01-09
Good morning.
My system have again with the new motherboard default stability "at cold".
"At cold", memtest86 on Live USB Ubuntu find errors.

---

### Post by sudodus on 2014-01-09
If you get only one error with memtest after several hours of testing, it is enough to say that there is bad RAM (or possibly a bad connection to the RAM).

There could be a crack or something that moves because of heat, and therefore acts differently cold and hot. If I understand correctly you have two memory cards, so test systematically with each one taken out until you find out which one is causing trouble. (If you have bad luck, the problem is on the motherboard, but I think chances are that one memory card is bad.)

---

### Post by utilisateursys on 2014-01-09
> **sudodus said:**
> If you get only one error with memtest after several hours of testing, it is enough to say that there is bad RAM (or possibly a bad connection to the RAM).

There could be a crack or something that moves because of heat, and therefore acts differently cold and hot. If I understand correctly you have two memory cards, so test systematically with each one taken out until you find out which one is causing trouble. (If you have bad luck, the problem is on the motherboard, but I think chances are that one memory card is bad.)
Good morning.
Thank you for your help.

I'll test "at cold" each memory on each DIMM socket...

---

### Post by utilisateursys on 2014-05-04
Good morning.

I spend my topic as solved because for six days I did not notice any problems more on my PC.
Here's what I did ...

_ 1 / I change the memory modules :_
Not wanting to change the CPU I decided to invest in a new memory kit (2 x 2 GB) of another brand .
I had a single mistake , every other day .
The manufacturer did send me a new kit, which works perfectly for six days.

** I deduced that it must be tested and be wary of new memories.**

_ 2 / Optional ?...I change the thermal paste :_
Everywhere is said to be necessary for the thermal paste gray one drop  ( size of rice) to the center of the processor and install the fan on  top.
Wanting to follow the instructions of the manufacturer, I was very surprised the difference in procedure.
In fact I had to pull a vertical line in the middle of the dough and  spread a mound processor (with a plastic card ) to the back of the fan.

_ 3 / Optional ?....I disable in the bios regarding the UEFI :_
Intel Rapid Start Technology : Disabled.
Intel Smart Connect Technology : Disabled.
Fast Boot : Disabled.
CSM : Enabled.
Secure Boot : other OS.

I'm imagine it did remove all messages of this type :
Could not write bytes : broken pipe...
Cannot set freq 16000 to EP 0X86
Cannot set freq 24000 to EP 0X86

---

### Post by sudodus on 2014-05-04
Congratulations and thank you for sharing what you did and your results :KS

---

