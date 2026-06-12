---
title: "ALi M5451 sound card prob"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by Liam on 2005-04-15
I don't have sound at all at the moment. On boot or when I try to restart alsa, here's what I get:

```

# /etc/init.d/alsa restart
 * Shutting down ALSA...
 * /etc/init.d/alsa: Warning: 'alsactl store' failed with error message 'alsactl: save_state:1194: No soundcards found...'.
Invalid card number.

```

It'll loop maybe a dozen times before quitting.

# lspci

```

0000:00:00.0 Host bridge: ALi Corporation M1621 (rev 01)
0000:00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (rev 01)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 5d)
0000:02:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)
0000:02:00.1 Serial controller: Xircom Cardbus Ethernet + 56k Modem (rev 03)

```

# lsmod | grep snd

```

snd_ali5451            21828  0
snd_ac97_codec         64608  1 snd_ali5451
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  1 snd_pcm

```

# grep ali /etc/modprobe.d/alsa-base

install snd-ali5451 modprobe --ignore-install snd-ali5451 && /lib/alsa/modprobe-post-install snd-ali5451

I've got a feeling that my problem is with that last bit, but I've got no idea what options I need to be passing to the driver.

Any ideas?

Thanks.

---

### Post by sunfisher on 2005-08-14
Did you ever get resolution on your audio problem? I have almost exactly the same indications and results. It seems clear there is no driver loaded for the ALi M5451 chipset. Thus far I haven't had any success on compiling and loading the ALSA driver set. My compile of the driver won't proceed because:
"The file /usr/src/linux/include/linux/version.h does not exist."
although I've downloaded the Linux source for linux-2.6.10.

---

### Post by Liam on 2005-11-01
Sheesh, I completely forgot about this, and it took me two and a half months to notice sunfisher's PM. I'll post my solution here, for the benefit of everybody else and google.

After a lot of digging on the ubuntu boards and elsewhere, I FINALLY got around to fixing this a couple of days ago.

Here's the steps I took:

[list=1]
[*]Upgraded to breezy via dist-upgrade; I couldn't get it to install from the CD
[*]Upgraded to latest 686 kernel in the repos - I can't remember which at the moment, the notebook is at home 
[*]Appended 
```

acpi_irq_isa=10 apm=off

```
to the line beginning with "# kopts" in /boot/grub/menu.lst. acpi_irq_isa should be your sound cards IRQ; mine's 10
[*]Ran update-grub
[*]Rebooted
[/list]

This gets me sound in XMMS, mplayer, and the xfce volume control; I haven't tried it with audacity or anything.

This is on a KDS Valiant 6480, BTW. YMMV.

---

### Post by Rollerbob on 2006-01-27
[QUOTE=Liam]Here's the steps I took:[/QUOTE]

I'm having exactly the same problems on a Toshiba Portege 4010 with a soundcard which has the Ali M5451 chipset.  I'd like to try this solution, but can you tell me how I get the IRQ of my sound card?

---

### Post by tritium3 on 2006-10-07
> **Rollerbob said:**
> I'm having exactly the same problems on a Toshiba Portege 4010 with a soundcard which has the Ali M5451 chipset.  I'd like to try this solution, but can you tell me how I get the IRQ of my sound card?
You can get the IRQ of all devices with "cat /proc/interrupts"

---

