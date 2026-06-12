---
title: "New CPU, witch one?"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by Tompalaz on 2007-12-28
Hello!

I'm about to buy a new CPU but i don't know witch one i should choose.
I'm thinking of Q6600 but is it worth it?

I have a motherboard that "only" support 1066Mhz, a P5W DH Deluxe.

I experiment with AMP, watching High Definition Videos and listen to music.

---

### Post by wripley on 2007-12-28
are you deadset on Intel?  personally, i don't have a preference, but my AMD rig beats the crap out of my buddies intel.  although i have had good results with both...

---

### Post by Tompalaz on 2007-12-28
yep, i'm in to intel. I just bought a new socket 775 motherboard.
well, my intel rig beats my friends AMD computers :P

---

### Post by tgalati4 on 2007-12-28
Do you really need a quad core?  A dual core will provide for 95% of your needs at 2/3's the power consumption.  A new E6750 dual core on a P35 Intel board with an nVidia 8600 GT card draws about 120 watts.  I imagine the quad core will draw close to 200 watts.  The dual cores are also quite a bit cheaper.

Get the fastest memory that your board supports.

---

### Post by Tompalaz on 2007-12-29
I thought of that, but, as i said, my board only support 1066Mhz, or do you know what happen if i overclock, could i run a 1333 CPU on a 1066 motherboard?

the fastest CPU (at least here in Sweden atm) that is a 1066Mhz CPU is a E4600.

---

### Post by tgalati4 on 2007-12-29
Don't know if you can run a 1333 Front Side Bus processor on a 1066 board.  Probably, but you won't get the rated speed, and the core voltages could be different so without trying I really don't know.

If you can afford a Quad Core and it supports 1066 FSB then go for it.  I don't know what power costs in Sweden, but here in Los Angeles at (11 cents US per kilowat) the difference in power consumption is probably $80/year for 24/7 use, or $50/year for 40-hour workweek use.

So unless you really need 4 processors, the extra power consumption after 3 years will cost you a graphics card or hard drive upgrade.  Both will give you better *hands on* performance.

Get a Western Digital Raptor disk drive (10,000 rpm) and an nVidia 8600 or 8800GT graphics card and that will give you a better desktop experience for the price difference between quad and duo core.  And this ignores the power savings.

It's your euro.

---

### Post by Tompalaz on 2007-12-29
google is your friend
2 300 Swedish kronor = 356.4172 U.S. dollars, thats what a Quad Q6600 cost, that is, what i know, the only quad core that is 1066Mhz/FSB

and at the moment i live at my parents home (i'm only 17 :P ) so they pay the bills :D

I thought of buying a 8800GT and 1gb memory, (total 3gb) but i must face the fact, that my cpu needs an upgrade.(if i want to enjoy High Definition)

I have 3 harddrives, i thinking about have my 2 - 200GB disks in RAID (striped) and then my /home on the third disk. Do you know if Ubuntu runs well in RAID?
I will buy a 8800Gt, some day. But i think i'll go for the Q6600 first though.

---

### Post by tgalati4 on 2007-12-30
Ubuntu can handle RAID fine, but you need to consider what you are going to use it for.  If you striped the disks for performance, you cut reliability in half.  If you mirror the disks, you get no speed improvement but you improve reliability (maybe) and you have twice the power consumption for the same storage space.

I would only set up RAID for a business-critical application.  For media streaming, it's really not needed.  400 GB for storage is more critical than retrieval or write speeds.  Unless you edit video for create 3D animation as a paid profession the time savings for striped RAID is not worth it.

Here in the US a similar Dual Core (E6750 2.66 GHz) is $210 US.  So that's a $146 difference.  Add the extra power consumption over 3 years and that's about ~$300 difference.  You can buy a nice Raptor boot disk for $200.

---

### Post by Tompalaz on 2007-12-30
It's just that the CPU you recommend is a 1333FSB processor, and my board only support 1066.
Here it's almost the same price for a E6X50 and a Quad Q6600 (and Q6600 isn't a 1333MHz processor)

And okay, i guess i'll skip the RAID.

Another OT question.
I made a new clean install of Ubuntu Studio (7.10), but now its much slower that before, and I'm having major instability problems with Emerald and Compiz.
Any idea what that can be?

---

### Post by Yellow Pasque on 2007-12-30
The board can support the 1333MHz CPU's with a BIOS update.
[http://support.asus.com/cpusupport/cpusupport.aspx](http://support.asus.com/cpusupport/cpusupport.aspx)

---

### Post by Tompalaz on 2007-12-30
Oh, that was really good news!!!
Do you think i should go for E6750 or E6850?
E6850 cost almost as much as the Quad core?
I guess i easely can clock up the E6750 to 3Ghz like the E6850 runs?!
I think i go for the E6750

---

### Post by Efros on 2007-12-30
Q6600 ocs very easily to 3 GHz, I use mine with a Zerotherm BTF90, CPU temps stay under 45C. I do a lot of video encoding, with judicious selection of codecs you can get multi-threaded apps working very effectively on a quad core. xvid multi-thread really steams as does ERMP.

---

### Post by Tompalaz on 2007-12-30
I have ordered a E6750 now :)

---

### Post by tgalati4 on 2008-01-01
Ubuntu Studio uses a REAL TIME kernel.  It is designed for single-purpose, workstation tasks, such as video animation or music recording.  Because the CPU cycles are dedicated to the processor and not you the user, the mouse and keyboard are laggy.  This is normal.  The real-time kernel is good for uninterrupted 2-hour recording of a church concert.  It's not good for browsing the web.  

I would recommend dual-booting and only using Studio when you really need it.

---

### Post by Tompalaz on 2008-01-05
> **tgalati4 said:**
> Ubuntu Studio uses a REAL TIME kernel.  It is designed for single-purpose, workstation tasks, such as video animation or music recording.  Because the CPU cycles are dedicated to the processor and not you the user, the mouse and keyboard are laggy.  This is normal.  The real-time kernel is good for uninterrupted 2-hour recording of a church concert.  It's not good for browsing the web.  

I would recommend dual-booting and only using Studio when you really need it.

I'm just using Ubuntu Studio because i think there isn't so much things installed from start.
What do you think i should dual-boot with, the "real" Ubuntu?

Anyhow, I flashed my bios, and it went really good. But when i installed my CPU bios says
that the speed is 2125Mhz and that the FSB speed is 1065Mhz, the new bios were supposed to fix this?!

---

### Post by Tompalaz on 2008-01-06
Okey, problem solved. I boot my machine and the cpu runs in 1333Mhz. I changed couple of things in bios.

---

### Post by Yellow Pasque on 2008-01-06
> **Tompalaz said:**
> Okey, problem solved. I boot my machine and the cpu runs in 1333Mhz. I changed couple of things in bios.

Cool.. I'm glad everything worked out for you.

---

