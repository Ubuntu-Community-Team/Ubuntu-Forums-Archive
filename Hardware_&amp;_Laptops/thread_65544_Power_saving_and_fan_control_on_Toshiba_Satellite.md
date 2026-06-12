---
title: "Power saving and fan control on Toshiba Satellite"
date: 2005-09-14
forum: Hardware &amp; Laptops
---

### Post by niels on 2005-09-14
Hi there..

I have a Toshiba Satellite A10 with Breezy installed which I use for my studying. It's 1½ years old. Normally I am only using Ubuntu, but I also have Windows XP installed.
I have two big problems, which prevent me from using Ubuntu and thereby forces me to use XP at my lectures. The problems is:

1) The battery is a bit old, so I would like the system to have some powersaving funktions when the battery gets low. I would like it to turn down the brightness, go to standby farster and other powersaving functions when the battery is used 75%, 50%, 25%, 10% or something like that. It would be nice to have a program to do it automaticly (only when it's on battery).

2) The fan is VERY noicy when I use Ubuntu. This is not a problem with XP, where it is totally quiet. Why is it so noicy? Is there any way I can make it as quiet as it is in XP? If I can't, I really can't use Ubuntu for my lectures - and how can i then convince my freinds to use Ubuntu?


Hopefully someone can help me...

Niels

---

### Post by jeegiz on 2005-09-14
I'm using Toshiba Satellite 1410-313 with Ubuntu Hoary. It is possible to enable power saving features from the Bios, including frequency of CPU fan start.

Additionaly I have installed fnfxd, which lets user to change LCD brightness, turn on/off fan, etc. with Fn+x combinations.

I guess toshiba_acpi kernel module is needed for the correct fnfxd functioning.

---

### Post by niels on 2005-09-15
[QUOTE=jeegiz]I'm using Toshiba Satellite 1410-313 with Ubuntu Hoary. It is possible to enable power saving features from the Bios, including frequency of CPU fan start.

Additionaly I have installed fnfxd, which lets user to change LCD brightness, turn on/off fan, etc. with Fn+x combinations.

I guess toshiba_acpi kernel module is needed for the correct fnfxd functioning.[/QUOTE]

I also have FnFx installed, and it seems to work.

How do I optimize my powersavings and make the fan quiet?

And just another thing:
What does the following FnFx commands do (I'm a computer hardware dommy):
- toggle cpu
- suspend to ram
- suspend to disk
How do I use it, and is there any dangers connected to the use of these features?

---

