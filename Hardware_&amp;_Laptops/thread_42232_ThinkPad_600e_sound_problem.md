---
title: "ThinkPad 600e sound problem"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by IbeeX on 2005-06-16
Hello

I am am not able to setup sound on my 600e laptop, I was googling for it and nothig helps ](*,)

I made in kernel boot noapic nolapic acpi=off amp=on, enabeled sound with ps2
made changes to /etc/modprobe.d/alsa-base
but when I try to insert sound module I gett error
# modprobe snd-cs4236
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.10-5-686/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device
and also there is no alsaconf in Ubuntu hoary and I hawe alsa-utils package installed,
is there somebay thet can help me! since sund is only thing that is still not working in my config. 

Please  

Ivan

---

### Post by tonyw50 on 2005-07-08
I also have no sound on Thinkpad 600E.  Newbie and don;t understand how to implement any of the suggestions gleaned from the forum.

---

