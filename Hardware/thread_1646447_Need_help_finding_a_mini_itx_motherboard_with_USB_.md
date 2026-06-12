---
title: "Need help finding a mini itx motherboard with USB 3.0 headers"
date: 2010-12-15
forum: Hardware
---

### Post by gpaper on 2010-12-15
I’m preparing to build my first Ubuntu computer, and I’m excited. One thing I wanted was a small-sized computer, and I found a great case. It limits me to a mini ITX motherboard. I found some great motherboards for it, 890GX-USB3, and GA-H55N-USB3, but I can’t find one that has everything I’m looking for, and I’m hoping for some help.
   
  I’m trying to find a Mini ITX motherboard that does the following:
   
  * Allows me to use DDR3 RAM at 1333Mhz, preferably upto 8GB
  * Has USB 3.0
  * Has a USB 3.0 header, so I can connect the front USB 3.0 ports on the front of the case without having to route a wire out of the box and into one of the back ports. (This is the one thing that I can’t find)
  * Preferably 6Gb/s SATA connects
   
  Since it’s a Mini ITX, I have only one PCI port. I know I could put in a USB 3.0 card that has internal ports, but I’d rather the motherboard have one, so I could use the one port for something else.
   
  I’d greatly appreciate any help.

---

### Post by cascade9 on 2010-12-16
> **gpaper said:**
> * Has a USB 3.0 header, so I can connect the front USB 3.0 ports on the front of the case without having to route a wire out of the box and into one of the back ports. (This is the one thing that I can&#8217;t find)

AFAIK, this is going to be be far your biggest issue. Asrock and ECS have started putting USB 3.0 headers on some motherboaords (the only ones I know of are the 890FX deluxe 4 and 890GX extreme 4). -

[http://www.asrock.com/mb/overview.de.asp?Model=890FX%20Deluxe4&cat=Specifications]("http://www.asrock.com/mb/overview.de.asp?Model=890FX%20Deluxe4&cat=Specifications")

[http://www.asrock.com/mb/overview.de.asp?Model=890GX%20Extreme4&cat=Specifications](http://www.asrock.com/mb/overview.de.asp?Model=890GX%20Extreme4&cat=Specifications)

The problem is that at least up till june/july (and still AFAIK) there was no common USB 3.0 pinout-

[http://www.semiaccurate.com/2010/06/08/asrock-and-ecs-comes-custom-usb-30-pin-header/](http://www.semiaccurate.com/2010/06/08/asrock-and-ecs-comes-custom-usb-30-pin-header/) 

So even if you get a motherboard with headers for USB 3.0, its almost certain that it wont work with the front panel USB 2.0 ports. You'd have to do some modding to make things work.

---

### Post by C.S.Cameron on 2010-12-16
Sounds like a fun project.

I have three computers with mini ITX MB's.
One is in a cigar box and another other squeezed into a muffin tin
The muffin tin one uses USB2 flash drives as HDDs.
One for XP and one for Ubuntu
I'm wondering if a PCI-USB3 card will fit in it.

Please keep us posted on your progress.

---

### Post by gpaper on 2010-12-16
Thank you for the help. It has been a fun learning experience.

My first, and only other computer I built was back in 2000 while I was in college. (I've purchased new laptops for my primary computer since.) But its time for a new desktop, and a lot has changed since then. I've been a Microsoft OS user since DOS, but I do a lot with web programming and use a Ubuntu server for hosting and have always wanted to become more comfortable with it. Plus, I've always been a fan of efficiency, and I don't like how sluggish Windows is. I figured this new computer would be an excellent start Ubuntu.

The [case]("http://www.lian-li.com/v2/en/product/product06.php?pr_index=545&cl_index=1&sc_index=26&ss_index=67&g=spec") has USB 3.0 ports on the front, but after reading the article posted about the pins, I'll have to see what the case uses. I just thought the internal and external connections looked the same. I guess not.

Unfortunately, it looks like Asrock does not have mini-ITX form factor motherboards.

What I'm planning on right now is to getting a nice system, but with two problems:

* The motherboard limiting the SSD to 3Gb/s instead of running at 6Gb/s
* Having to run a cable out an opening in back and into the back of the motherboard (if thats the type of pin for it)

Maybe in a year I could upgrade the motherboard if there is one released with the features I need.

---

### Post by cascade9 on 2010-12-17
> **gpaper said:**
> My first, and only other computer I built was back in 2000 while I was in college. (I've purchased new laptops for my primary computer since.) But its time for a new desktop, and a lot has changed since then. I've been a Microsoft OS user since DOS, but I do a lot with web programming and use a Ubuntu server for hosting and have always wanted to become more comfortable with it. Plus, I've always been a fan of efficiency, and I don't like how sluggish Windows is. I figured this new computer would be an excellent start Ubuntu.

The [case]("http://www.lian-li.com/v2/en/product/product06.php?pr_index=545&cl_index=1&sc_index=26&ss_index=67&g=spec") has USB 3.0 ports on the front, but after reading the article posted about the pins, I'll have to see what the case uses. I just thought the internal and external connections looked the same. I guess not.

Unfortunately, it looks like Asrock does not have mini-ITX form factor motherboards.


Long time no build, eh? 

I'd seriously think about a MicroATX case and board. If you want mini-ITX and USB 3.0 for HDDs/flash drives (I cant imagine that you'd want it for anything else) then eSATA might be a better way to go. Shouldnt be to hard to find a mini-ITX case with a front mounted eSATA port. 

Checking the user manual on the PC-Q11 shows normal USB 2.0 pinouts for the front mounted USB ports. 

I wouldnt be to upset about no asrock miniITX motherboards. From all the examples I've seen, asrock isnt that great.

---

### Post by gpaper on 2010-12-17
I had looked at Micro-ATX cases a few days ago, since there seems to be a better selection of motherboards. But that was called off after looking at the hideous cases for them. I  know for me, I really have my heart set on the Q11 case, even for what it limits me to.

I guess the search for USB 3.0 was because I was looking at a smaller version of the case, the Q07. That wouldn't let me have more than one HD, which would be a big issue for me. That was relieved when I found the Q11, and the fact that it did have USB 3.0 was very nice, but not something I'll be using right now.

From reading all the reviews and looking at the pictures, the case does have USB 3.0, but it has an additional cable to convert it to USB 2.0 to plug into a USB 2.0 motherboard header. Else, I would have the cables run out through the PCI port, with an included special plate, and use both the USB 3.0 ports in back.

After all the help, and with more research, I'm thinking that the GA-H55N-USB3 is the best way for me to go right now, and that I might look at upgrading the motherboard in a year if something is out better suiting my needs.

Thank you very much.

---

### Post by fjgaude on 2011-01-03
> **gpaper said:**
> 
After all the help, and with more research, I'm thinking that the GA-H55N-USB3 is the best way for me to go right now, and that I might look at upgrading the motherboard in a year if something is out better suiting my needs.

Thank you very much.

I've done about what you have done: research! I've ordered the Lian Li Q11 today from Newegg, with the gigabyte ga-h55n usb3 motherboard, w/ i5-655 CPU. It seems the best and latest of the advanced, power boards. I also ordred the SilverStone ST45FSF small foot print 450w power supply. That PS I think will do the trick with cooling fan issues and cables.

If I can't get the Intel HD video to work with Ubuntu 10.10 I'll install a nVidia GeForce 210 PCIe x16 board.

I'll report back how things go!

---

### Post by Grace999 on 2011-01-11
There are hardly motherboard in current market have usb 3.0,you can use a usb 3.0 font panel:_to_ enjoy the usb 3.0 speed.:popcorn:

---

### Post by fjgaude on 2011-01-16
Finished, well, just about, with the Gigabyte GA-H55N USB3, Lian-Li PC-Q11 build. All work just fine as I stated earlier. Very quiet, just above a whisper. Overclocking to 3.6MHz with ease. No heat issues with stock fans.

Video is better than expected, the Intel GMA HD works fine with HD video DVDs and graphic design programs. Sound is excellant. All running under Ubuntu 10.10 and 11.04 Alpha.

Only issue: the box will not suspend or hibernate. Still working with the BIOS to see if changes there will support the suspend function.

So iTA motherboards are great for the desktop, and not for the deskunder. <smile>

Any questions?

---

### Post by C.S.Cameron on 2011-01-16
That is a nice looking Mini ITX.

---

### Post by fjgaude on 2011-01-16
It is said to be and looks very high quality. Gagabyte does good design and work. The CPU socket is said to handle 95 watts. That's beyond the overclock of the Intel i5s. Can't say about the i7s.

---

### Post by fjgaude on 2011-01-16
It is said to be and looks very high quality. Gigabyte does good design and work. The CPU socket is said to handle 95 watts. That's beyond the overclock of the Intel i5s. Can't say about the i7s.

---

### Post by fjgaude on 2011-01-16
It is said to be and looks very high quality. Gigabyte does good design and work. The CPU socket is said to handle 95 watts. That's beyond the overclock of the Intel i5s. Can't say about the i7s.

---

### Post by C.S.Cameron on 2011-01-16
So the big question:

Does the BIOS boot USB3?

---

### Post by fjgaude on 2011-01-16
> **C.S.Cameron said:**
> So the big question:

Does the BIOS boot USB3?

Don't know because I have no USB3 device to test, but the BIOS allows the USB3 to be active, so...

---

### Post by grahammechanical on 2011-01-16
Have you looked at [http://www.mini-itx.com?](http://www.mini-itx.com?) Might give ideas of what is available.

Regards.

---

### Post by cascade9 on 2011-01-17
> **fjgaude said:**
> It is said to be and looks very high quality. Gagabyte does good design and work. The CPU socket is said to handle 95 watts. That's beyond the overclock of the Intel i5s. Can't say about the i7s.

i5s go to 95watts TDP without overclocking (i5-750, i5-760). Overclocked, they can eat a lot more than that.

---

### Post by fjgaude on 2011-01-17
> **cascade9 said:**
> i5s go to 95watts TDP without overclocking (i5-750, i5-760). Overclocked, they can eat a lot more than that.

Thanks for this info. I don't go with quads but I'm sure others do. The Gigabyte MB I guess can handle power in the 150 watt range. I'm sure my little box wouldn't like the heat. At 3.6KHz and full stress the CPU temp goes to 55C, using Linux **stress** program. Not bad for a quiet box using a low-profile fan: SILVERSTONE NT07-1156 90mm CPU Cooler. It is said to be good for 95 watts with the i5, i7. The fan goes from 1200 to 3000 RPM. At 1200 it cannot be heard on the desktop, just barely at 1800. I haven't let it go to 3000 yet. <smile>

---

### Post by cascade9 on 2011-01-17
Looking at that board, I wouldnt be pushing it. Just not enough power control. Not like you bought it for overclocking, so its not a problem :D 

BTW, I dont think that 150watts of sysem consumption would really be possible with that CPU (its an i3 the but power consumption would be very similar to your i5)- 

[http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking_9.html#sect0](http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking_9.html#sect0)

The next page has the same figures for an i7 860. ;) 

Wait a sec.....I dont know 'stress' but if you are getting 3.6GHz with stress, its only using a single core. Still 55C isnt bad. 

Looking at that setup, I would be really temped to get a cheap heatpipe heatsink and tring to bend the heatpipes so that the cooler stuck up between the power supply and fan. Thats probbly just me, most people would be happy @ 55C and walk away. ;)

[http://www.bit-tech.net/hardware/cases/2010/10/08/lian-li-pc-q11-mini-itx-case-review/1](http://www.bit-tech.net/hardware/cases/2010/10/08/lian-li-pc-q11-mini-itx-case-review/1)

---

### Post by fjgaude on 2011-01-17
Thanks for the links... I've seen the one from bit-tech before I bought the Q11.

I'm running at 4.0MHz right now with no issues. The Intel pwr mgr is so good it keeps the cores at 3.2 until there is work and then it jumps to the 4.0. The VCore voltage goes from .97 to 1.225v.

The **stress** program is Linux, under Ubuntu. Has all the features one would need for testing all the hardware, memory, hdd, i/o, and cpu.

I use gkrell to watch the fans and the CPUs along with everything else. Under load all CPU  threads are loaded 100%, so I'm sure the temps I gave you are essentially correct.

My goal is to get the quietest, fastest box I can. I need the quiet the most. I think I'm about there! <smile>

---

### Post by jadechessink on 2012-02-09
hello sir, i have sort of skimmed through this thread and thought that it was worth mentioning a motherboard that i am currently using. it is 1.8 ghz and has usb 3.0 as well as 6gb sata connection. 

[http://www.amazon.com/gp/product/B004WO8OA8/ref=oh_o04_s00_i00_details](http://www.amazon.com/gp/product/B004WO8OA8/ref=oh_o04_s00_i00_details)

---

### Post by jadechessink on 2012-02-09
hello sir, i have sort of skimmed through this thread and thought that it was worth mentioning a motherboard that i am currently using. it is 1.8 ghz and has usb 3.0 as well as 6gb sata connection. 

[http://www.amazon.com/gp/product/B004WO8OA8/ref=oh_o04_s00_i00_details](http://www.amazon.com/gp/product/B004WO8OA8/ref=oh_o04_s00_i00_details)

---

