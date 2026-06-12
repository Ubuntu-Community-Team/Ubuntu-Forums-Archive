---
title: "PS/2 and USB problems"
date: 2009-01-15
forum: Hardware
---

### Post by leilong on 2009-01-15
I hope this is in the right thread, as I am new. I apologize for my Noob-ish-ness in advance. This may be a "stupid question" but I have about a 3rd Grade level knowledge base in Unix.

This is a hardware issue for a *desktop*, but I didn't see a "Hardware & Desktops" Section, so I'm thinking that those are 2 separate subjects in one thread. Here's my problem:

I recently put together a PC and pilfered a blank drive out of another PC, and instead of shilling out $100 for a brand-new copy of Windows XP, I loaded Ubuntu on it.

I bought the components separately, and physically put it together myself.

After I got the beast running, I encountered a strange problem with my ports not wanting to work.

First, here are my specs:
I have Ubuntu 8.10 installed
The motherboard in question is GA-M61PME-S2
It has Mouse and Keyboard PS/2 ports that are *not functioning* at the moment.
It has 4 USB ports mounted in that are *not functioning* at the moment.
It has 2 sockets to add front-side USB ports. In the F_USB1 slot, is the 2 USB ports built into the case. These are *not functioning* at the moment.
In the F_USB2 slot, is a Card Reader I purchased to fill in the floppy drive slot. It supports 4 different memory card types, and has a USB port built in. *This is the only functioning USB port on the computer.*

Fortunately, I had an old iMac USB keyboard sitting around with 2 USB ports built into it, so I USB-ed the keyboard to the working slot, and fed the mouse into the keyboard. 

This works for me to troubleshoot, but this computer was purchased to give my mother a machine to surf the net, write up papers on, and store her digital camera pics to. She has a PS/2 keyboard, a USB mouse, a USB printer, and will want to be able to plug in her digital camera via USB as well. 

I'm sure that the printer and camera drivers will be easy enough to find (and a challenge for me to install =D), but it's all for naught if I have to tell her 50 million specific instructions that she'll have to try and remember just to make her computer function.

I searched the site, but it seems that PS/2 ports are typically a plug-and-play issue, which for some reason on my system it's not. If anyone knows a way I can check to see if these basic drivers exist, or where to find them if they don't, it would be very helpful.

_New Update_
A friend who is more knowledgeable in Ubuntu told me that perhaps I should check the BIOS settings to see if there is something I can edit in there to help with the situation. Keep in mind that my only way of I/O is a USB keyboard... which doesn't register on the system until Ubuntu is starting up, so I can't hit Delete right after starting the computer to enter into BIOS. So to check the settings there, I need some way of accessing the BIOS from within Ubuntu, or a way to make the keyboard function without Ubuntu loaded.

---

### Post by sandy8925 on 2009-01-15
I don't think you can access the BIOS from Ubuntu. But for the other thing if you have a BIOS option called 'USB legacy device' enable it and you might be able to access the BIOS then. Unfortunately you need BIOS access to enable it but you can't access the BIOS in the first place.

I guess you should try installing some other OS (or use a Live CD) and see if the PS/2 works on that.

---

### Post by sandy8925 on 2009-01-15
Also , the pins on the PS/2 keyboard that you tried might have bent. CHeck that.

---

### Post by leilong on 2009-01-15
The keyboard is fine, I have a USB to PS/2 converter as well, this also did not work to make the mouse function. I have an old optical mouse that has a nice red laser that could light the whole room, and this did not even power on when connected to the USB ports, or the PS/2 with converter. I'm still working on finding a way to get the BIOS up. It's only a matter of time.

I have the Win XP restore disk for my old computer, so maybe I'll do an illigit install long enough to see if that can help.

Any more ideas anybody has would still be appreciated. :P

---

### Post by AKADAP on 2009-01-15
Get a known working PS2 keyboard.
If you can't access the bios with that, send the motherboard back as it is broken.
Only worry about Linux being the problem if you can access the bios with the keyboard, but the keyboard stops working once Linux starts running.

---

### Post by leilong on 2009-01-15
Problem Solved?

So I'm writing this on a PS/2 keyboard, that let me into the BIOS, the Legacy USB was on, the BIOS was set to better accomodate USB keyboards, all 7 USB ports work, and the computer functions as it should.

What did I change?

***_The Monitor._***

I noticed that the computer was having a very unique problem that it would only start the first time after being unplugged from a power source if the monitor was unplugged, and so I decided to try the keyboard while I couldn't see anything. Num Lock lit up immediately, I thought Cool, and then plugged the monitor in, only to have the keyboard shut off.:confused:

I proceeded to pull my old CRT monitor out of my bedroom, plugged it in, and I'm functioning with no problems at all now.

The monitor I was using was an old ViewSonic LCD monitor, which seemed to work just fine, but apparently has some interesting personal issues...

So for anyone encountering a port problem on the motherboard, try a different monitor?:confused::confused:

---

