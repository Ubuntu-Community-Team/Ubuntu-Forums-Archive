---
title: "Texas Instruments 6 in 1 Card Reader from hell not working . Help wanted."
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by v_oo_v on 2005-10-05
Hello everybody,
I have a 6 in 1 reader integrated on my Laptop.
Laptop: HP pavilion 4165EA (4000 series).
This is the output of lspci:
[I]0000:06:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:06.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:06.3 Unknown mass storage controller: Texas Instruments:  Unknown device 8033
0000:06:06.4 0805: Texas Instruments: Unknown device 8034[/I]
It simply seems that the whole Texas Instruments From Hell devices, chipset or whatever it is does not work...:???: 
I have surfed for a while and did not found nothing appropriate about this issue. I read about a WSBD driver but following all steps given on their website ([http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd](http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd)) , I am almost sure that this is not the case...
Anyone could help me about this, or give me a link? It’s really tedious booting on windows when I need to access a SD/MMC card, use a PCMCIA slot or connect a FireWire device (I’m currently using the laptop for ALL of this things.).
Thanks in advance.

---

### Post by JLB on 2005-10-05
I Have a HP laptop with the card reader too. TI has not released any info on these. HP can't help you either. get an external USB reader.

---

### Post by John.Michael.Kane on 2005-10-05
Said TI device requires a special firmware in order for the card reader to work.

---

### Post by v_oo_v on 2005-10-05
](*,) Yargh!
¿And does anybody know how to load the firmware?. ¿Is there any HOWTO or FAQ?.
Thanks,
v_oo_v

---

### Post by JuanC on 2005-10-05
I also have a HP Compaq Laptop , and actually there is no way to use it.

---

### Post by raghav_p on 2005-10-06
yea.. there are no linux drivers for it yet.

---

