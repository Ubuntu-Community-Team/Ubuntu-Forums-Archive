---
title: "Yamaha OPL3SA2 ubuntu 10.10"
date: 2010-11-02
forum: Hardware
---

### Post by spiderdijon on 2010-11-02
Hello, I have been fighting with this Toshiba 4000cdt (very old laptop) everything works fine except the sound. It has a Yamaha OPL3SA2 chip. I have tried everything I can find about getting this sound card to work including

- Boot with acpi=off and isapnp=off   [Thread here]("http://ohioloco.ubuntuforums.org/showthread.php?p=543301")
- modprobing with all the additional parameters 
```
modprobe snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530
``` 
those settings are correct I checked the bios.

The modprobe doesnt complain but lsmod shows nothing using it. PNP is not on in the bios. Apparently alsaconf used to provide a very simple and easy way to get it working but obviously thats no longer around.

If anyone can help this laptop get a 2nd (probably 7th or 8th :)) life it would be great.

---

