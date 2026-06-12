---
title: "Headphone does not mute speaker"
date: 2008-11-13
forum: Hardware
---

### Post by chauraph on 2008-11-13
Hi, I am facing a problem that many are facing...
When I pluged my headphone in the speaker did not mute.
I've checked the Alsa mixer, I cannot mute the speaker individually, when I mute any of the channel, both the headphone and the speaker are muted.

I am using Ubuntu 8.10 on my NEC Versa 3500 laptop.


for the specs, see [here]("http://www.nec-computers-ap.com/hk/products/product.aspx?CID=16&tab=1&cuid=1&mid=265").

the model of the audio chip is "Realtek High Definition Audio ALC888"

> kin@kin-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec: Motorola Si3054
Codec: Generic 8086 ID 2802
kin@kin-laptop:~$ 

I searched through this forum and find that the solution is to add a option specifying the model of the laptop in "/etc/modprobe.d/alsa-base".

like 
> options snd-hda-intel model=ACER

when I check the ALSA documentation, what I got is: 

> ALC883/888
858		  3stack-dig	3-jack with SPDIF I/O
859		  6stack-dig	6-jack digital with SPDIF I/O
860		  3stack-6ch    3-jack 6-channel
861		  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
862		  6stack-dig-demo  6-jack digital for Intel demo board
863		  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
864		  acer-aspire	Acer Aspire 9810
865		  medion	Medion Laptops
866		  medion-md2	Medion MD2
867		  targa-dig	Targa/MSI
868		  targa-2ch-dig	Targs/MSI with 2-channel
869		  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
870		  lenovo-101e	Lenovo 101E
871		  lenovo-nb0763	Lenovo NB0763
872		  lenovo-ms7195-dig Lenovo MS7195
873		  haier-w66	Haier W66
874		  6stack-hp	HP machines with 6stack (Nettle boards)
875		  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
876		  6stack-dell	Dell machines with 6stack (Inspiron 530)
877		  mitac		Mitac 8252D
878		  auto		auto-config reading BIOS (default)


I can't find my vendor and model. 
I've tried to use "NEC" but not work at all.

My laptop's configuration is like this : one jack for headphone and SPDIF, one jack for microphone and one stereo internal speaker. Which value should I set to  "/etc/modprobe.d/alsa-base"?

thanks

---

### Post by tstduke on 2009-10-07
I have a NEC Versa p9210 and I have the same problem. I find there are lots of sound issues with my laptop and Ubuntu 9.04. I think it might be due to the fact that the laptop has 4 speakers and a sub built into it.

---

