---
title: "Edgy on Acer Aspire 1693WLMi"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by nw_raptor on 2006-11-03
I give up! I cannot get it to boot. Dapper didn't even require special boot params, but Edgy seems to be picky.

So far I've tried:
noapic, nolapic, acpi=off, irqpoll pci biosirq, vga=771, vg1=791.

In one case, it threw me at a prompt about initramfs.

It just freezes. I thought I'd give the text-mode a go, but that froze during package installation.

Any ideas?

---

### Post by sylverwing on 2006-11-10
Hoi nw_raptor,

first of all i'm not a expert on this but I have a Aspire 1694WLMi.

I don't know what your problem just is but if its a black screen then this worked for me.

Put the cd in and when startup screen shows select F6 Other Options
I added this at the end of the line

```
vga=771 noapic
```

then you get the Ubuntu logo with the horizontal progressbar

After a while the screens goes black and you see nothing.
I wait until the cd stops spinning and everything is quiet :D 
I even heared the startup sound but I still can't see a thing.
Next press the following keys

ctrl+alt+F1

this is the terminal and you type th folowing;

```
sudo nano /etc/X11/xorg.conf
```

then with the arrowkeys or PageDown key go down to the Device section and ad this

Option "MonitorLayout" "LVDS, AUTO"

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        **Option "MonitorLayout" "LVDS, AUTO"**
EndSection
```


then type "crtl+x" (to close the 'xorg.conf' file),
then type "Y" (to save modified)
then hit "enter" (to confirm)

and now the magic, type;

```
sudo killall -9 Xorg
```

Now the desktop from Edgy should be appearing.

I asume you have the ATI X700 and after your installation you will probably have to install the fglrx driver.

If this is not a anwser to your question I hope this could be usefull to some one else.

Good luck ;) 

PS: sorry for any bad english

---

