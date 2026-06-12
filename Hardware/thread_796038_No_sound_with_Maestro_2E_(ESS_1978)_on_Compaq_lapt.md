---
title: "No sound with Maestro 2E (ESS 1978) on Compaq laptop"
date: 2008-05-16
forum: Hardware
---

### Post by llevering on 2008-05-16
I am trying to install Xubuntu (first 7.10 now 8.04) on a Compaq Armada V300 laptop. Almost everything is working fine, except the sound. When I looked on the internet I found that almost anyone who installed Linux on this laptop didn't have any problems, but this is not the case with me.

Yesterday I followed the general sound problems FAQ and tried everything, but once you've loaded the right kernel module they assume it will work from there, however that is not the case.

lspci gives as output (for the soundcard):
```
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
```

This sound card will need the snd-es1968 kernel module (found on the website of the alsa project and on sites of other people describing how to install Linux on this type of notebook). So I checked if Ubuntu loads this module with: lsmod | grep snd-es1968. This gave the following output:

```

snd_es1968             30592  0 
gameport               16008  1 snd_es1968
snd_ac97_codec        101028  1 snd_es1968
snd_pcm                78596  3 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_es1968,snd_pcm
snd_mpu401_uart         9728  1 snd_es1968
snd                    56996  12 
snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```

None the less aplay -l still gives the following output:
```

aplay: device_list:205: no soundscards found...

```

And alsamixer also gives an error saying there is no soundcard with the name dafault. Who has an idea and can help me out?

---

### Post by jabjoe on 2009-01-21
Hi,

Did you get any where with this?

I've got the same issue. Sound has worked with other distros (PCLinux and Vector).

I've not given up yet, but if you have cracked it already, would love to know. :-)

Joe

---

### Post by Sonsum on 2009-01-21
I'm kind of new to linux myself, so I'm not sure what to say...
Are you sure you did everything right?

Because I followed the procedure for the same soundcard on my Toshiba Portege 7020CT Laptop and the sound works beautifully.

---

### Post by llevering on 2009-01-22
No sorry I never found out anything more than what is in the first post. The laptop has been given away to people who are typing on it very happily.

---

### Post by jabjoe on 2009-01-22
Thanks for letting me know. Just for anyone else, I get:

[   49.524850] ES1968 (ESS Maestro) 0000:00:0c.0: found PCI INT A -> IRQ 11
[   49.528080] ES1968 (ESS Maestro) 0000:00:0c.0: sharing IRQ 11 with 0000:00:05.2
[   51.076060] AC'97 0 does not respond - RESET
[   51.079781] AC'97 0 access error (not audio or modem codec)
[   51.083627] ES1968 (ESS Maestro): probe of 0000:00:0c.0 failed with error -13

from dmesg

The 0000:00:05.2 device is the network card. I'm thinking the driver isn't happy sharing IRQ 11. The BIOS doesn't let me manually assign interrupts. Still playing, I'll post any updates.


Joe

---

### Post by jabjoe on 2009-01-24
Hi Sonsum,

Sorry, didn't see your response. This is a TOSHIBA PORTEGE 7140CT. Interesting.

All I did was install Xubuntu and set it to use the LXDE desktop. Only now trying to get sound working.

I've been through "Comprehensive Sound Problem Solutions Guide v0.5e" now, didn't help. :-(

Can you give me your kernel boot parameters from /boot/grub/menu.1st ?

You add anything to /etc/modules or /etc/modprobe.d/alsa-base ? If so, what?

What about your BIOS PCI IRQ and PnP settings?

Cheers for any info.

Joe

---

### Post by jabjoe on 2009-04-08
ok, I swear I tried this before, but, a kernel update took out all the kernel boot options I had in my menu.lst file, and sound sprang to life!

Maybe the options I had for getting acpi working where messing it up, but I thought I had tried all the combinations trying to get acpi and sound working, so I'm wondering if it was fixed (possibly incidentally).

Either way with just a simple acpi=force (I know I tried that before) and I now have sound and shutdown working fine so I'm happy.

Joe

---

