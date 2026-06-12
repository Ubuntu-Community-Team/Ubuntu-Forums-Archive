---
title: "Which Shuttle SFF XPC AMD Socket 939 machine?"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by maubp on 2006-08-14
My old shuttle has died after about six years of solid service (running just Ubuntu for the last year or so), and I want to buy a new machine.  I'd like to go dual core, and based on the current prices that means one of the following AMD Socket 939 systems:

[SN95G5V3](http://eu.shuttle.com/en/desktopdefault.aspx/searchcall-12/searchcategory-369/noblendout-1/tabid-72/170_read-11848/), about 180 GBP (plus graphics card)
Max 2gb RAM, 184-pin DIMM modules
2 x Serial ATA, 2 x IDE ATA 133 drives, 1 x floppy disk drive
1 x AGP, 1 x PCI, 1 x serial port (COM)
No onboard graphics
Black

[SN21G5](http://eu.shuttle.com/en/desktopdefault.aspx/searchcall-12/searchcategory-369/noblendout-1/tabid-72/170_read-12437/),  about 190 GBP
Max 2gb RAM, 184-pin DIMM modules
2 x Serial-ATA, 1 x IDE ATA 133, 1 x floppy disk drive
1 x PCI-Express, 1 x PCI, 1 x serial port (COM)
NVIDIA GeForce 6100 GPU
Black

[ST20G5](http://eu.shuttle.com/en/desktopdefault.aspx/tabid-72/170_read-10719/), about 260 GBP
shuttle link
Max 2gb RAM, 184-pin DIMM modules 
2 x Serial-ATA, 1 x IDE ATA 133 drives, 1 x floppy disk drive
1 x PCI-Express, 1 x PCI, No serial port (COM)
ATi RADEON XPRESS 200 3D
Silver 

I would be using an IDE CD/DVD burner and an IDE 200gb hard drive initially.  I might add a SATA drive later...

I would be buying 2gb of RAM soon (but I might re-use my old 1x256mb and 1x512mb for a while to spread the cost).

I don't really care about the graphics performance, I just need  1280x1024 to run my 17 inch flat screen.  Of course, having good 3D driver support would be nice.

I would be happy with plain stereo audio out.

Searching the forum I've seen a comment by **e_james** about needing boot options "noapic nolapic acpi=off" for the ST20G5, and **netztier** said something about "noapic" to get the on board ethernet to work on the SN95Gv3 (nForce3 Chipset).

**Which of these three would you guys recommend for use with Ubuntu Linux?**

**Is the AMD 64 version of Ubuntu going to cause me trouble?**

---

### Post by sgtBiafra on 2006-08-14
I would recommend the SN95G5V3... tried and true hardware that will run Ubuntu rather well (I've got a V2 at home). I know many people have had issues with running Ubuntu on cutting edge hardware, and those weren't even Shuttle SFF systems (that tend to be about 200-300% more finnicky).

As far as the A64 version of Ubuntu, it shouldn't cause you many problems as the repositories have the 64-bit versions of pretty much all you could want. I don't personally run it at home even though I have a 64-bit chip as I needed to run WINE and it was less complicated to get it running on a 32-bit architecture.

---

### Post by maubp on 2006-08-14
I'm a little cautious about being too cutting edge.  I'd like a soon to-be-released SK22G2 with its AMD Socket AM2 an support for up to 4gb of RAM, but the board graphics sound like they would be asking for trouble on Linux: It uses the "brand new" DeltaChrome chipset.

Anyway, with the SN95G5V3 there is no on board graphics, so I'd need an AGP graphics card.

I run a 1280x1024 flat screen.  I don't play much in the way of games. It might be fun to try some of the "GUI candy" that cutting edge linux can offer, but I'm not fussed.  Support for dual display might be nice.

I'd be looking for:
* will work well with both 32bit and 64bit Ubuntu.
* passively cooled (less noise) but won't get too hot
* cheap (ideally under 50 GBP)

Looking at Dabs.com there are lots of NVIDIA GeForce or ATi Radeon cards at this price range.

Thanks :)

P.S. Anything to beware of with the SN95G5V3 - should the on board LAN, USB, audio etc "just work"?

P.P.S. I would like to use a USB keyboard.

---

### Post by patwack on 2006-08-15
i have a shuttle SN21G5 sitting downstairs, using it as a mythtv box running dapper, install and setup went flawlessly, everything just works

---

### Post by maubp on 2006-08-15
Good news that the SN21G5 works fine - and no messing about with trying to decided on a graphics card.

I see the NVIDIA GeForce 6100 GPU (the on board graphics for the SN21G5) is [supported on Linux by nVidia](http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-a.html), and listed as [working with XGL](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#nVidia_Cards).  It also looks like its [supported by the open source nv driver](http://ftp.x.org/pub/X11R7.0/doc/html/nv.4.html) too.

Do you use the nv driver or nVidia's binary driver?  Do you have 3D acceleration?

---

### Post by sgtBiafra on 2006-08-15
I would recommend getting an nVidia card just for the ease of setup (it still seems that the ATI drivers are a bit more flaky). For your purposes (light gaming and desktop use @ 1280x1024), a passive-cooled 6100 or 6200 would be fine but I'm not sure what the conversion of the price would be (~$40 USD).

Here are the issues I had with my SN95G5v2:
* CPU support. The v2 has issues with newer E6 stepping chips (not a problem for v3).
* added "noacpi" to the boot parameters to force detection of on-board network adapter (though I now use a PCI-based wireless NIC).

Other than that, everything else was pretty easy. All of my USB ports and the on-board audio work just fine. I'm currently using both a USB mouse and keyboard and an external drive for backups.

Yes, I do have 3d acceleration working through nVidia's driver (the nvidia-glx package). The nv driver is only sufficient for 2d work in my opinion.

---

### Post by maubp on 2006-08-15
Thinking of the SN95G5V3 here, I can get an *MSI GeForce FX5200 128MB* model [FX5200-TD128LF](http://msicomputer.co.uk/Products.aspx?product_id=703745&cat_id=78) for only £25 which appears to be passively cooled with both VGA and DVI outputs, as well as TV out.  Even if they send me the very similarly named [FX5200-TD128](http://msicomputer.co.uk/Products.aspx?product_id=703441&cat_id=78)  that also looks fine.

Or, this *Inno3D GeForce 6200 128MB* model (DabsValue) [inno3d GeForce 6200](http://www.inno3d.com/products/graphic_card/gf6_agp/6200.htm) also £25 appears to be passively cooled with both VGA and DVI outputs, as well as TV out. 

Neither is fastest card in the world, but as far as I can tell it should be fine for Linux and should cope with XGL at a push.  Fingers crossed it will fit fine in the Shuttle case.

I've been looking at dabs.com as their Shuttle prices are competive, and their CPU prices are about normal.  I'd rather make on single order as then its easier to point fingers if something doesn't work.

Its just a pain that Dabs' graphics card listings don't make it clear when a VGA port is included - and I need that for my current flat screen monitor.

Dabs.com also don't mention if their cards have a fan or not - there was a Gigabyte card that looked fine but after finding the product code on the Gigabyte website and finding a picture, it looks like it has a fan included.  And an extra fan = more noise :(

---

### Post by maubp on 2006-08-16
It was a tough call between the SN21G5 and the SN95G5V3 but I figured they should have fixed most of the niggles in a product by V3.

I went with Scan.co.uk rather than Dabs.com because (a) Dabs didn't have the CPU in stock right now, and (b) Scan do a much better job of marking their graphics cards a passive or fan cooled.  Once postage was included it made sense to do one single order rather than a pix-n-mix between them.

I've ordered the Shuttle SN95G5 V3, Athlon 64 X2 4600+, and a passively cooled AGP graphics card - a 256MB XFX GeForece 6200.

I'll put it together this weekend, using my hard drive, DVD burner and my old RAM.  Once my credit card has recovered (which might be a while - the car is due for its service and needs a wheel bearing changed) then I'll get a matched pair of 1gb sticks of RAM.  I'll let you know how it goes.

**Update**:
Got the bits, and put it together but it won't boot.  Apparently some of the socket 939 Shuttles are very fussy about their memory, and it looks like it doesn't like my old RAM.

I've ordered the new pair of 1gb sticks of RAM and fingers crossed then it will boot up.

**Update 2**:
Got the new RAM, no difference.  I'm now guessing that its due to the unit shipping with an older BIOS that does not like my fairly recent dual core CPU.  Trying to send it back to the dealer now :(

**Update 3**:
Found a friend with an old single core socket 939 chip, and used that to boot up and then flash the BIOS.  Now it does recognise my dual core chip :)

I've had a quick play with the ubuntu amd64 "live CD" and will install to the hard disk shortly.  The CD failed a checksum so I'm re-downloading it first.

Basic sound, graphics, network, and USB all just worked :)

I have not yet tried: IDE hard drives, SATA/RAID hard drives, 3D acceleration, power saving, suspend/resume, firewire support, surround sound, digitial audio in/out, or the serial port.

**Update 4**
Installed Ubuntu to the hard drive now, and installed the SMP kernel, mp3 support and a few other bits and pieces.  Got both cores showing up now - it wasn't obvious how to test this using just the live CD.

I've also installed the [lm-sensors](http://www.lm-sensors.org/) bits (this machine has the NVIDIA nForce3 250Gb chipset) including the sensors-applet package, and added a CPU sensor to the panel.  Oddly enough it only offers me one reading, which looks about right for the CPU as claimed.  The BIOS however shows by both a CPU temp and a System temp too.

I'll have a go following [this thread](http://www.ubuntuforums.org/showthread.php?t=2780).

I know the IDE hard drive supports SMART for temperature monitoring, but I haven't got that to work yet either.

---

### Post by maubp on 2006-08-25
First of all, after installing hddtemp and rebooting, the "Sensors Applet" was able to show me my drive temperature.

Then I set to work on the motherboard sensors...

Running gives "lspci -v" lots of stuff including:

[b]0000:00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device a551
        Flags: 66MHz, fast devsel, IRQ 3
        I/O ports at ff00 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <available only to root>[/b]

Running "sensors-detect" gives:

[b]Driver `lm85' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 4c40'
    Busdriver `i2c-nforce2', I2C address 0x2e
    Chip `Analog Devices ADM1027, ADT7460 or ADT7463' (confidence: 8 )

Driver `ds1621' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 4c40'
    Busdriver `i2c-nforce2', I2C address 0x4e
    Chip `Dallas Semiconductor DS1621' (confidence: 3)

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 4c00'
    Busdriver `i2c-nforce2', I2C address 0x50
    Chip `SPD EEPROM' (confidence: 8 )
  * Bus `SMBus nForce2 adapter at 4c00'
    Busdriver `i2c-nforce2', I2C address 0x51
    Chip `SPD EEPROM' (confidence: 8 )
  * Bus `SMBus nForce2 adapter at 4c00'
    Busdriver `i2c-nforce2', I2C address 0x53
    Chip `SPD EEPROM' (confidence: 1)

Driver `it87' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `ITE 8712F Super IO Sensors' (confidence: 9)
[/b]

After letting it set things up, I have this

[b]maubp@shuttle2:~$ sensors
ds1621-i2c-1-4e
Adapter: SMBus nForce2 adapter at 4c40
temp:      +0.00°C  (low  =  +0.0°C, high =  +0.0°C)

adt7463-i2c-1-2e
Adapter: SMBus nForce2 adapter at 4c40
V1.5:      +0.000 V  (min =  +0.00 V, max =  +3.32 V)
VCore:     +0.003 V  (min =  +0.00 V, max =  +2.99 V)
V3.3:      +3.309 V  (min =  +0.00 V, max =  +4.38 V)
V5:       +0.020 V  (min =  +0.00 V, max =  +6.64 V)
V12:      +0.000 V  (min =  +0.00 V, max = +15.94 V)
CPU_Fan:    805 RPM  (min =    0 RPM)
fan2:         0 RPM  (min =    0 RPM)
fan3:         0 RPM  (min =    0 RPM)
fan4:        -1 RPM  (min =    0 RPM)
CPU:      +46.00°C  (low  =  -127°C, high =  +127°C)
Board:    +38.25°C  (low  =  -127°C, high =  +127°C)
Remote:   +28.00°C  (low  =  -127°C, high =   +80°C)
CPU_PWM:    40
Fan2_PWM:  255
Fan3_PWM:  255
vid:      +0.000 V  (VRM Version 2.4)
[/b]

Some of those numbers look fine :)

---

