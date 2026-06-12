---
title: "Screwed Up Sound Card"
date: 2012-02-21
forum: Hardware
---

### Post by dodle on 2012-02-21
I was trying to get a TV tuner to work by following some instructions to use the modprobe command. Now the system doesn't recognize my sound card. I don't remember exactly what the commands were that I used. Is there a way to use modprobe to get my sound card working again? This is the card I am using:

> :~$ lspci | grep -i "audio"
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

> :~$ uname -r
2.6.32-5-686

**----- EDIT -----**

I don't know if this helps, but here is some other info:

/etc/modprobe.d/alsa-base.conf:
> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7
# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; /sbin/modprobe --quiet snd-seq ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 && { /sbin/modprobe --quiet snd-emu10k1-synth ; : ; }

# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

dmesg:
> :~$ dmesg | grep -i "audio"
[    7.456360] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[    7.456517] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64

:~$ dmesg | grep -i "alsa"
[    6.300990] saa7134 ALSA driver for DMA sound loaded
[    6.301042] saa7133[0]/alsa: saa7133[0] at 0xe4008000 irq 16 registered as card -1

the saa7134 driver is my TV tuner.

---

### Post by dodle on 2012-04-05
*bump*

I am on Debian 6, but so far have not been able to solve the problem in the [Debian forums](http://forums.debian.net).

**----- SOLVED -----**

I'm not sure what fixed it but here is what I did: I renamed [color=red]/etc/modprobe.d/alsa-base.conf[/color] and [color=red]/etc/modprobe.d/alsa-base-blacklist.conf[/color] then I removed [color=red]alsa-base[/color] and restarted. Then I reinstalled [color=red]alsa-base[/color] and restarted again and it was working. I'm not sure renaming the files did anything because after everything was working I renamed them back and restarted and it didn't affect anything. So I think just removing and reinstalling [color=red]alsa-base[/color] did the trick.

---

