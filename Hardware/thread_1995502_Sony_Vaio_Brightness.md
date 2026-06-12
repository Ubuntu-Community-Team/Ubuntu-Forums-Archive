---
title: "Sony Vaio Brightness"
date: 2012-06-03
forum: Hardware
---

### Post by Aapcosta on 2012-06-03
Hi,

first of all sorry if the answer to my question I'm gonna submit.

I recently installed ubuntu 12.04(64 bit) on my Sony Vaio, almost everything is working as intended. But I can't adjust the brightness on my laptop( a necessity to save power). When using the fn keys in combination with f5 and f6 I can see the adjustment bubble but the brightness doesn't changes. Where when adjust my volume everything works as intended.

I've tried the following two "solutions" I've found on the forums. None of them worked.

[I]sudo gedit /etc/X11/xorg.conf
And then find the Section "Device" and add the bold line.
Section "Device"
Identifier "Default Device"
Option "NoLogo" "True"
Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection

1. sudo gedit /etc/default/grub
2. Change the line GRUB_CMDLINE_LINUX="" into
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
3. sudo update-grub
4. Restart your linux[/I]

I've a Sony Vaio with i3 processor, no graphics card, but an integrated graphic chip (sandybridge).

It's driving me nuts that I can't find a working solution for this. I hope anyone of the ubuntu community can help me with this.

Thanks in advance.

---

### Post by Redblade20XX on 2012-06-03
Instead of in the second method
```
*acpi_osi=Linux*
```

Try,
```
acpi_backlight=vendor
```

-Red

---

### Post by Aapcosta on 2012-06-04
Changing:

acpi_osi=Linux  for  acpi_backlight=vendor

sadly didn't worked. 

Thanks anyways for the help

---

### Post by agindre on 2012-06-18
Have you tried this solution : [http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup) ?

Power Management section

---

### Post by cosmicbuff on 2012-06-23
I am not running an ubuntu install right now, but I think the basics are the same,
I have VPCEG25EN , its a core i3 2330M with integrated intel HD graphics , it doesnt have  nVIDIA card.

I was unlucky with (acpi...=vendor and acpi....=linux) at boot.

So any other methods now..?

---

### Post by Redblade20XX on 2012-06-23
> **cosmicbuff said:**
> I am not running an ubuntu install right now, but I think the basics are the same,
I have VPCEG25EN , its a core i3 2330M with integrated intel HD graphics , it doesnt have  nVIDIA card.

I was unlucky with (acpi...=vendor and acpi....=linux) at boot.

So any other methods now..?

Do you want to control the brightness or automatically set it to the lowest value on boot?

-Red

---

### Post by cosmicbuff on 2012-06-27
> **Redblade20XX said:**
> Do you want to control the brightness or automatically set it to the lowest value on boot?

-Red
I want to control brightness and set brightness levels to my profiles , because I use them a lot ,. 
any solutions?

---

### Post by cosmicbuff on 2012-06-29
Phew !

Managed a half baked method

I did a root  edit to 

```
/sys/class/backlight/intel_backlight/brightness 
```It defaults value at 4882

I changed it to 2441 and saved changes , Voila my brightness reduced to half,, I am ok with it till a better method comes out , till then i will keep editing..

vaio is making it difficult..

---

