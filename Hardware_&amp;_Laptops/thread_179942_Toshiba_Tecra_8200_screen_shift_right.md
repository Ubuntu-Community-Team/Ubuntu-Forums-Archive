---
title: "Toshiba Tecra 8200 screen shift right"
date: 2006-05-21
forum: Hardware &amp; Laptops
---

### Post by mich_r on 2006-05-21
Hi
I have Toshiba Tecra 8200 laptop with Trident CyberBladeXP graphics card and I have screen shifted right about 2-3 pixels. I have googled long time, tried many things with no success.
Here's my Device section from xorg.conf:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"trident"
	ChipSet		"BladeXP"
	Option		"XvHsync" "-3"
	BusID		"PCI:1:0:0"
EndSection
```

First of all - xvidtune makes no change to the screen. When clicking Test or Apply there is a quick "blink" on the screen and it goes back to the old look.

Second - I tried "vesa" instead of "trident" - with it the screen is displayed _perfectly_ so it is not a hardware problem. But this is not a solution for me - vesa performance is poor, and there is no xv support

I tried many things - HSkew at Monitor-Mode section, LcdCenter Option at the device section, FixPanelSize, UseModeline ..... no luck.

Please, help me, it makes me mad ](*,)

---

### Post by homersbrain on 2006-05-21
My Trident CyberbladeXP in my toshibe laptop doesn't suffer from this problem. Maybe it's because you have "Generic Video Card"  identified.

Here is mine:

Section "Device"
	Identifier	"Trident Microsystems CyberBlade/XP"
	Driver		"trident"
	BusID		"PCI:1:0:0"

Worth a try.

---

### Post by mich_r on 2006-05-22
Thx homersbrain, I will try it in the evening.

In the meantime I've found a thread about exact problem @linuxquestions - it seems the poster found a solution, but unfortunatelly I cannot understand it :( Could you please explain it to me, what exactly he has done (I will post a request @ linuxquestions too, but because it was about a month ago I'm not sure to receive an ansver there)

here is the thread: [http://www.linuxquestions.org/questions/showthread.php?t=196431]("http://www.linuxquestions.org/questions/showthread.php?t=196431")

and there is a solution I can't understand:
> I broke down and downloaded knoppix to see if it would work any better. Everything on the laptop was configure perfectly, Knoppix is really amazing. Anyway, I copied the XF86Config file from knoppix to my hard drive, rebooted, and I still had the same problem.  arghh.

The only difference I could remember was that knoppix ran a framebuffer to the proper resolution when it booted. I edited my grub config to boot at 1024x768, rebooted and everything works great now.

---

### Post by homersbrain on 2006-05-23
Ok, I had a quick look at that post - it's quite old so there probably won't be an answer. Here is my take on it:

Edit your menu.lst by going to a terminal and:

```
sudo gedit /boot/grub/menu.lst
```

Find the 'defoptions' part and edit it so it looks like:

```
defoptions=quiet splash vga=791 scheduler=cfg
```

Save the file then, in the terminal:

```
sudo update-grub
```

Reboot, and see if it helped. The vga=791 should make it boot at 1024x768.

Hope it works for you.

---

### Post by mich_r on 2006-05-23
It works! It works! I can't belive that :D 

FYI - the identifier made no difference (IMHO it is only a kind of alias and do not affects the driver behavior)

I could not to deal with "update-grub", it constantly deleted the "defoptions" line from menu.lst, but I googled some for "defoptions grub" and finally found that it is the same like adding "vga=792" ( or 791 for 64K colors ) to the kernel line. Here's an extract from my menu.lst:
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot
```

then I ran
```
sudo grub-install /dev/hda
```

rebooted, and ... we are at home :mrgreen: 

The same as eolson from LQ I have no idea what relation between boot logo resolution and screen centering is , but - the most important thing is that it just works.

Great thanks homersbrain, without your tips I would be stick with this problem for weeks... months ... maybe longer, who knows ;)

---

### Post by Trinisan on 2006-06-16
Thanks guys, was about to reinstall windows on the tecra 8200 i had, but found this in time. I will try these options. I didn't want to show off Ubuntu
with a weird looking screen.

---

