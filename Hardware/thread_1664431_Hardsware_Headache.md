---
title: "Hardsware Headache"
date: 2011-01-10
forum: Hardware
---

### Post by ububaba on 2011-01-10
Actually it is more than a headache. I discovered a blue so 
called 10pin (in reality only 9pins) USB adapter on the "floor" 
of the chassis. Despite several tries, can't figure out where 
was it sitting originally. 

It says NC, GND, P2+, P2-, +5V on one side, and on the other 
face it says, +5V, P1-, P1+, GND.

I am trying to guess what problems could it have created.

1. At the GRUB menu, I can't press any key, thus can not
select anything. Rebooting has not helped neither has the
change of HDs. 3 green lights do appear at the beginning 
of boot, but not when the GRUB appears. The countdown is
not seen as well. One can go on waiting but nothing takes 
place after that. How can this stage be by passed?

2. Some other hassle which has not been discovered yet.

Any suggestions? Advice? Or recommendations for solution?

Would be very thankful.

---

### Post by pbpersson on 2011-01-11
You say this is a USB connector, presumably because the other end goes to a USB jack on the back of your machine.

You should plug your keyboard into another USB jack and not use that one.

.....or am I missing something?

I checked my motherboard manual and those do sound like USB connections.  Do you have your manual or can you download it from the web?  That would tell you where on the motherboard that should be connected.

---

### Post by ububaba on 2011-01-11
> **pbpersson said:**
> You say this is a USB connector, presumably because the other end goes to a USB jack on the back of your machine.

You should plug your keyboard into another USB jack and not use that one.

.....or am I missing something?

I checked my motherboard manual and those do sound like USB connections.  Do you have your manual or can you download it from the web?  That would tell you where on the motherboard that should be connected.

Thank you very much for your response. I do have the relevant 
manual. And have as I mentioned earlier, tried to plug it in the
possible places. It did not have any effect that I could notice.
We can assume that it was reserved for future use. 

The overhanging problem remains, that is to get the computer to 
work. (Obviously I am using another machine for this correspondence. 
Any ideas about that?

---

### Post by pbpersson on 2011-01-11
Try a different keyboard, try a PS/2 keyboard instead of USB, pull out the hard drives and try booting from CD.

Those are three ideas.

If none of those work it might be the motherboard is fried - it happens sometimes.

---

### Post by Yellow Pasque on 2011-01-12
Those USB headers are usually on the bottom of the mobo (behind and/or below the last PCI slot). If one falls off, it really shouldn't cause any issues.

Before assuming hardware issues, try a LiveCD.

---

### Post by [Snc] on 2011-01-12
> **Temüjin said:**
> Those USB headers are usually on the bottom of the mobo (behind and/or below the last PCI slot). If one falls off, it really shouldn't cause any issues.

Before assuming hardware issues, try a LiveCD.

Also you should check the BIOS for "on board" or "front side" USB ports, make sure they are enabled.

PS. some technicians or repairmen do a really bad yob putting the computer together, i once got a machine from a service with no cables connected inside, not even the power to the mobo (and a warranty seal-label attached to the back, which i had to destroy to see that)

---

### Post by ububaba on 2011-01-12
There are two different issues here.
1. The USB adapter
2. The freezing of the keyboard.

I talked of them in the same breath hoping/assuming that 
there could be a connection between them. Apparently not.
As I get stuck with the grub screen (being locked/frozen) 
I cannot proceed any further i.e. even to the Recovery Mode.
No LiveCD or memory stick is recognised by the machine.
Can't enter the BIOS.
I could very well have "disturbed" something while blowing 
the dust away. The only person to be blamed is me.

Thanks for all the suggested cures, which I have applied. 
No betterment. I am hoping that someone who has suffered 
the same setback reads this.

---

### Post by ububaba on 2011-01-12
There are two different issues here.
1. The USB adapter
2. The freezing of the keyboard.

I talked of them in the same breath hoping/assuming that 
there could be a connection between them. Apparently not.
As I get stuck with the grub screen (being locked/frozen) 
I cannot proceed any further i.e. even to the Recovery Mode.
No LiveCD or memory stick is recognised by the machine.
Can't enter the BIOS.
I could very well have "disturbed" something while blowing 
the dust away. The only person to be blamed is me.

Thanks for all the suggested cures, which I have applied. 
No betterment. I am hoping that someone who has suffered 
the same setback reads this.

---

### Post by ububaba on 2011-01-12
There are two different issues here.
1. The USB adapter
2. The freezing of the keyboard.

I talked of them in the same breath hoping/assuming that
there could be a connection between them. Apparently not.
As I get stuck with the grub screen (being locked/frozen)
I cannot proceed any further i.e. even to the Recovery Mode.
No LiveCD or memory stick is recognised by the machine.
Can't enter the BIOS.
I could very well have "disturbed" something while blowing
the dust away. The only person to be blamed is me.

Thanks for all the suggested cures, which I have applied.
No betterment. I am hoping that someone who has suffered
the same setback reads this.

---

