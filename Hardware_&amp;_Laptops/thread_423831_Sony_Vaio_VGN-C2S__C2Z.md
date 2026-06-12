---
title: "Sony Vaio VGN-C2S / C2Z"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2007-04-26
Hi, does anybody have experience with Ubuntu running on a Sony Vaio VGN-C2S and/or C2Z notebook? I want to get a new one and I have an eye on them, they look great, have good hardware and have a reasonable price. Is everything well supported? The most important thing to me is proper suspend/hibernate and WLAN support. I'd appreciate if you share your experiences!

Tom

---

### Post by el3ktro on 2007-05-03
So there's not a single person running Ubuntu on this laptop!?

---

### Post by whirl on 2007-05-26
I have my eye on VGN-C2Z/B  and Dell XPS M1210

If anyone is using vaio of any sort preferably VGN-C2Z/B please do leave your comment of the product.

o/

---

### Post by StueyB on 2007-06-29
I have a VGN-C2S and it *ALL* works out the box fine on 7.04 and most of it even works on 6.x also.

Have had NO bother whatsoever with it under Ubuntu.

---

### Post by sebbex on 2007-07-08
I installed ubuntu on my Sony Vaio VGN-C2S and I experience problems with the sound, if I plug in my headphones the laptop speakers still go, its very frustrating. Fortunately that is my only problem! :) However if anybody knows how to fix this please post a reply! Thanks! ^^

---

### Post by StueyB on 2007-07-10
Sebbex,

My C2S works fine with audio. Just a thought, have you tried a BIOS update at all ? I mean my machine was bought 3 weeks ago so I assume the BIOS is the latest available. Just trying to help!

---

### Post by sebbex on 2007-07-29
No.. How do I do that? Sorry to ask. :s

---

### Post by lundatok on 2007-08-03
Try enabling Jack Sense in the mixer settings.

---

### Post by il_ventu on 2007-12-20
> **sebbex said:**
> I installed ubuntu on my Sony Vaio VGN-C2S and I experience problems with the sound, if I plug in my headphones the laptop speakers still go, its very frustrating. Fortunately that is my only problem! :) However if anybody knows how to fix this please post a reply! Thanks! ^^
I'm experiencing the same problem with VGN-C2Z, do you have found any solution?
Thanks in advance.

Ciao
a

---

### Post by qstraza on 2008-06-04
i have vgn-c2z for a while now...
i had 3 releases on it. With Feisty i had problems with sound, with headphones, but this wasnt so bad, i just muted it in kmix... THe problem is, that the FN keys didnt work. With new release of ubuntu, hardy hanson that is, the sound problem is no longer a problem:p and FN key for volume work as well, but brightness still doesnt. Suspend to disk and ram works with hardy but i didnt work on feisty for me...

Another problem that i have noticed with feisty and hardy is about eta of the battery. Sometime it says 10h sometime 2h... it bounces like hell, but now on hardy it gets even further, if i remove the battery (hardware), hardy still shows it it taskbar, or if i start the vaio withouth the battery, hardy shows like i have the battery pluged in...

Anything else works uber kul;>
if anyone has any info on those thingies... let me know:p

---

### Post by diogosales on 2008-06-27
I have a VGN C2Z and I can't run Ubuntu 8.04 at all.
I tried to Run live cd, but not even the splash appears - some acpi error on console.
I tried installing right from ubuntu boot cd menu, no success either, freezes after just a bit.
Wubi I haven't tried yet, but does anyone have a problem with this model? I have all updates in order.

Thanks!

---

### Post by qstraza on 2008-06-28
try booting your ubuntu withount "quite" argument, or run it in safe mode, which is without "quite", if this works, install it and afterwards change the /boot/grub/menu.lst (removing "quite" argument)

---

### Post by dalma. on 2008-07-13
> **diogosales said:**
> I have a VGN C2Z and I can't run Ubuntu 8.04 at all.
I tried to Run live cd, but not even the splash appears - some acpi error on console.
I tried installing right from ubuntu boot cd menu, no success either, freezes after just a bit.
Wubi I haven't tried yet, but does anyone have a problem with this model? I have all updates in order.

Thanks!

Hi,

i have a vgn-c2z and installed ubuntu a few days ago.

What i did is the following:

- i downloaded the 8.04 image to my d drive and downloaded wubi as well. Everything with vista.
- i created an extra partition for ubuntu.
- i started wubi and selected my newly created partition (within vista)
- then i had to reboot

- from the dual boot menu, i chose ubuntu and i got an error:
[B]
ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1 
ACPI: EC: read timeout, command = 128[/B]

I rebooted again, chose ubuntu from the dualboot options and then hit a FN key (forgot which one it was, but it's shown on the screen).

From the available options i chose the second one. It had something to do with ACPI. If you had problems with ACPI errors then choose the second option

so I did.

Ubuntu installed and I was able to login into the system. What are problems now:

everything works except for:

- microphone. i can't figure out the microphone.
- shutdown doesn't work. It hangs with some kind of network manager error. This has been a problem with lots of computers with 8.0.4. I tried lots of things changing the menu.lst and changing the login window (shutdown/reboot) commands...but without any result.

wireless is working great. rebooting is working good. 

But the microphone and shutdown problems are annoying me bigtime. I'm using skype all day long and now i'm forced to use that stupid vista again.

I also don't have any laptop options in ubuntu, like power management, i don't see the battery indicator. When i install it, it does not work. I don't have sleep and hibernate option.

I think this has everything to do with the ACPI=OFF and the first time i installed ubuntu when choosing the second option, because the first option didn't work for me at all.

Well, maybe one of you knows what my problem exactly is.

---

