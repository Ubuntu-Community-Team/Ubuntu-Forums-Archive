---
title: "Excessive Fan or Hard Disk since upgrade to 12.04"
date: 2012-06-08
forum: Hardware
---

### Post by ravisghosh on 2012-06-08
Since upgrade to 12.04, I have been noticing excessive fan noise in my Dell 1555 laptop. I have dual boot and upon logging in Windows Vista, I don't find any noise and the laptop is calm.

Here is the output of sensors command.

> acpitz-virtual-0
Adapter: Virtual device
temp1:        +51.0°C  (crit = +100.0°C)
temp2:        +59.0°C  (crit = +100.0°C)
temp3:        +79.0°C  (crit = +100.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +80.0°C 

Is there a way to figure out which application is causing it and how can it be prevented?

---

### Post by daniaix on 2012-06-13
I encounter the same problem, which kind of graphics you have on your computer? 

is this helpful?

[http://ubuntuforums.org/showthread.php?t=1930450&highlight=fan](http://ubuntuforums.org/showthread.php?t=1930450&highlight=fan)

---

### Post by |{urse on 2012-06-13
Hopefully you also have windows installed on that laptop.

If so, update the bios. (triple check to make sure this is indeed your model)

[http://www.dell.com/support/drivers/us/en/04/DriverDetails/DriverFileFormats?c=us&s=bsd&cs=04&l=en&DriverId=R247639](http://www.dell.com/support/drivers/us/en/04/DriverDetails/DriverFileFormats?c=us&s=bsd&cs=04&l=en&DriverId=R247639)

If that doesn't help try this.

[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

If that still doesn't help switch to the fglrx driver, should cool your graphics chip down on that model.

---

### Post by ravisghosh on 2012-06-14
I installed fglrx-update from synaptic as I was unable to install it from Additional Drivers. Now, the laptop is much less hot and the fan doesn't make noise at all. However, I still have lower battery backup compared to Windows.

Today, I am going to update bios as you guys suggested and see how it works.

But I couldn't understand what is this DSDT thingi. I am not getting any errors as such.

---

### Post by ravisghosh on 2012-06-14
I just updated the BIOS and the fan noise is back :(

Then I removed fglrx-updates and installed fglrx to see if that had any effect. After that, I ran > aticonfig --initial to get the proper xorg file. 

Surprisingly, the noise was almost inaudible!

However, soon Unity crashed and now upon login all I would get is the desktop without launcher or panel. I could launch terminal by > Ctrl+Alt+T.

It seemed like xorg was getting corrupted and I tried > aticonfig --initial, but this time, I was greated with > sudo: aticonfig: command not found.

Now, I am reinstalling fglrx to see if it can help, but can't understanding why Unity is crashing and aticonfig refuses to run.

---

