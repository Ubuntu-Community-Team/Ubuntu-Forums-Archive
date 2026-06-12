---
title: "Asus EAH6850 v2 driver"
date: 2011-06-24
forum: Hardware
---

### Post by matepaco on 2011-06-24
Sorry for my english...

I've got a problem with my new Asus 6850 V2 (it's different from v1 spec, it has 2 power connectors and perhaps something else...).
It works with my windows only if i use the driver i found in the cd. With official amd driver or new driver from asus site i see the blue screen. In the cd there is the 8.782 driver (10.10?).
Now i'm trying to install it on my Ubuntu 10.10 maverick 64 bit. (it works with amd driver and my integrated 4290 card)
I've already tryed:
amd driver with buildpkg: 11.6 11.5 11.2 10.10
and driver whit automatic install: 11.6
amd driver from restricted driver manager
My 6850 doesn't work. I've got every time a console login an a complete purge of the driver.
I tried everything i've found on this forum and on italian forum.
Some ideas?
I've 4 days to activate RMA if it is broken...

Sorry for my english...

---

### Post by matepaco on 2011-06-25
Anyone?
Asus support tells me to wait for a new bios, but motherboard bios or vga bios? I don't know.
I'm waiting for a new reply from asus.

But it is a problem of all 6850v2 or it's simply a standard response and they have no idea what the problem is?

And waiting for the bios, any idea for install a driver that can make me use the correct resolution (1440x900)

---

### Post by matepaco on 2011-06-26
:( Up! :(

---

### Post by conradin on 2011-06-26
Stay calm, your English is fine.
That has an AMD GPU yes?
Have you looked into the proprietary hardware driver?
You can only boot to the terminal is that correct?
Im pretty sure that the Graphics card is just branded ASUS and that its more likely Some ATI Devices. So we need to know a bit more about that hardware:
```

sudo lshw > someFile

```
Then post the "someFile" here.

Also, have you tried the AMD Driver Download site:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by Yellow Pasque on 2011-06-26
> **matepaco said:**
> But it is a problem of all 6850v2 or it's simply a standard response and they have no idea what the problem is?
Most likely, they have no idea. The only thing I can suggest is making sure you have a good PSU and double checking all of the connections. If you're feeling up to it, remove and reinsert the card.

EDIT: I guess memtest wouldn't hurt to verify your RAM.

---

### Post by matepaco on 2011-06-26
> **conradin said:**
> Stay calm, your English is fine.
That has an AMD GPU yes?
Have you looked into the proprietary hardware driver?
You can only boot to the terminal is that correct?
Im pretty sure that the Graphics card is just branded ASUS and that its more likely Some ATI Devices. So we need to know a bit more about that hardware:
```

sudo lshw > someFile

```Then post the "someFile" here.

Also, have you tried the AMD Driver Download site:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I think it is a 6850 chip on a 6870 pci.
Proprietary hardware driver doesn't work.
Driver from AMD Driver Download site doesn't work. I tried 11.6 11.5 11.2 and 10.10 CCC with buildpkg option and 11.6 whit automatic install option.
I upload 2 file in a copressed archive:
myhardware <- lshw output
myhardwarepci <- lspci -v output

[QUOTE=Temüjin]Most likely, they have no idea. The only thing I can suggest is making  sure you have a good PSU and double checking all of the connections. If  you're feeling up to it, remove and reinsert the card.

EDIT: I guess memtest wouldn't hurt to verify your RAM.     [/QUOTE]
I've already used on my pc a powercolor 4870 pcs+ and an xfx 9800gt xxx. My PSU is a corsair vx 450. So i think it is powerful enough.
I'll do a memtest, but my ram never had problem.

Perhaps I'll have to RMA my video card?

---

### Post by matepaco on 2011-06-27
Memtest passed.
I removed the card and now I use the HD4290 (integrated in mobo). I installed catalyst 11.6 on win7 and Ubuntu (10.10 and 10.04) without any problem.
Today I'll reinsert the 6850...

What have I to do on linux?
Re-build fglrx, reconfigure it, or I have to do only a 
```
sudo aticonfig --initial -f
```

---

### Post by thane1 on 2011-06-27
I just purchased an Asus EAH6850 Radeon/AMD card today and I'm also stuck.  Also purchased a good quality 600W power supply.  Problems getting video and eventually reinstalled old Sparkle nvidia card.  Worked ok, so its not the power supply.  Reinstalled the Asus card and problems again.  

Reinstalled nvidia Sparkle card to regain video, removed nvidia proprietary driver, reinstalled ubuntu 10.10 eventually and it worked, but at a maximum resolution of 1280 x 1024.  However as soon as I installed the proprietary ATI/AMD FGLRX graphics driver, I lost the video and couldn't get it back.
I've now reinstalled 10.10 once more and I have video to a maximum of 1280 x 1024 again.  

I'm using dual monitors - 27" hdmi main monitor (was running on nvidia at about 1900+ x 1280 I think and a 22" lcd also.  Both are running at present although the 27" really needs more resolution.

Any chance there's another proprietary driver, which might work with this card?  Sounds like the original poster and I are both driver challenged.  Thanks,  cheers

---

### Post by thane1 on 2011-06-28
Returned the radeon card, paid the 5% restocking fee and bought a nvidia card.  All's well now.

---

### Post by matepaco on 2011-06-28
I also contact my e-shop to ask what to do... I'm waiting for a response.

Asus support says to wait for a new vga firmware and driver...

Every month AMD releases a new driver, but what about the bios/firmware?

Now I'm using the integrated AMD 4290 and the new 6850 is in its box:(

---

### Post by thane1 on 2011-06-28
matepaco;
     I had no success on repeated attempts to get the radeon card to work.  This morning I flashed the motherboard bios.  But the driver still locked the video up.  So I just cut my losses and went for a new nvidia card, as I didn't know how long it might be, before there was a workable driver available for the radeon.  I won't try radeon cards again for some time, I'm afraid to say.  Cheers.  Hope you get yours working.

---

### Post by matepaco on 2011-06-29
Thanks thane1,
but...
...where did you find the bios?

---

### Post by thane1 on 2011-06-29
matepaco;
    It was the motherboard bios, that I flashed not the Asus video card bios.  Found it on the mobo manufacturer's most local (to me) website under the support and download section.  My mobo was about a year old, so I didn't mind flashing it.  I don't think I'd personally risk flashing a brand new video card's bios though, unless the card manufacturer told you that was, what you needed to do.  Just my opinion. 

If you do decide to flash the bios, follow the manufacturer's instructions on how to do it to the letter and DON'T turn the power off during the process, or you could junk your board.  Cheers

---

### Post by matepaco on 2011-08-14
A month after:
New driver AND a new bios configuration (mobo)... and it works! :D

I had a bad bios configuration. I try to explain for all that have an 890gx mobo like me (Asrock extreme3).

So I've used the integrated graphic for a year with the 128MB of integrated sideport memory and 512MB of shared memory.
I've forced the mobo to use always 512MB and not the AUTO option that chose automatically from 32MB to 512MB.
When I installed the 6850, I chose the PCI-Express like primary graphic adapter and only the 128MB of sideport memory for the integrated graphic card (standard way to turn of the integrated graphic card).
But I haven't turn to AUTO the shared memory. It happened because when I chose the sideport memory only the option to chose how to share memory disappeared, but remained active.
So I choose to use shared mamory and sideport, then I choose AUTO on shared memory (now visible), then I choose again sideport only.
Now my 6850 uses only its memory and not the shared whit wich is not compatible.

I hope that my experience can be useful for someone.
Another 1 or 2 week of testing and I change the title of the thread to solved.

Thank you! :D

---

### Post by matepaco on 2011-08-23
Another new driver (catalyst 11.8) and it works!

Solved!

---

