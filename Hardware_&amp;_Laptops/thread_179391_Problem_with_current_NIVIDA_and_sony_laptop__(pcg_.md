---
title: "Problem with current NIVIDA and sony laptop  (pcg grt270("
date: 2006-05-19
forum: Hardware &amp; Laptops
---

### Post by mikebern on 2006-05-19
I used to be able to connect a crt/project to the vga port of the laptop and then 
power it up. When doing this both the LCD panel and the VGA port become active
from the boot the machine and inside X. With the current dapper release I no longer
see this. What happens is the boot screen show on both LCD and VGA port. Once
X start running I lose the LCD display but VGA port become active.

I would like to restore the option to have both the LCD panel and VGA port active showing the same content.

The NVIDIA driver doc talk about hot keys. The hot key do not work and never worked under linux.

Is there any way to make both port active and showing the same content ?

---

### Post by snipe122 on 2006-05-21
to fix this problem you need to configure twinview as long as you have a nvidia-card.

try to modify you xorg.conf:

add this:

Section "Device" (just add to the end of this section)

	Option		"TwinView"		"true"
	Option		"MetaModes" "1024x768,1024x768"
	Option 		"TwinViewOrientation" "Clone"

EndSection


be aware of choosing the appropriate resolution for your lcd and crt, should be both same.


greetz
snipe

---

