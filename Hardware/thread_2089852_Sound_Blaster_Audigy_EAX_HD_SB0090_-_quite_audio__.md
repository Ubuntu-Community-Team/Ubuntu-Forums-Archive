---
title: "Sound Blaster Audigy EAX HD SB0090 - quite audio / low quality"
date: 2012-11-30
forum: Hardware
---

### Post by seba22 on 2012-11-30
Hello,

Today i move my Audigy (I)  Sound Blaster Audigy EAX HD SB0090  from Windows PC (win 7) to linux Ubuntu 12.10  64bit

After plugging i was surprised it detect it just like that and i was able to hear Ubuntu welcome song.
So fare so good i think.

So i play music... ekhh
it's damn quiet !
It's sound somehow wrong... like in bathroom... sound it's not clear!

I change card to SB Live (old) work perfect.
Go with SB0090 to Windows PC Win7 work perfect.
Go with SB0090 to (other computer) Linux mint (i don't remember waht number) same issue... quiet, sound suppressed...

For example (on same headphones) on Windows 30% audio volume, give same result as 100% on Linux... but on Linux sound is have distortion 

If anyone have any idea... please share!
I try blacklist snd_emu10k1, but after reboot no sound.

```
alan@alan-OEM:~$ hwinfo --sound
24: PCI 401.0: 0401 Multimedia audio controller                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1102_4
  Unique ID: dtXw.trsEqNGuZ00
  Parent ID: 6NW+.rh8hKbvnT61
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:04:01.0
  SysFS BusID: 0000:04:01.0
  Hardware Class: sound
  Model: "Creative SB0090 Audigy Player"
  Vendor: pci 0x1102 "Creative Labs"
  Device: pci 0x0004 "SB Audigy"
  SubVendor: pci 0x1102 "Creative Labs"
  SubDevice: pci 0x0051 "SB0090 Audigy Player"
  Revision: 0x03
  Driver: "snd_emu10k1"
  Driver Modules: "snd_emu10k1"
  I/O Ports: 0xdf00-0xdf1f (rw)
  IRQ: 18 (23851 events)
  Module Alias: "pci:v00001102d00000004sv00001102sd00000051bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_emu10k1 is active
    Driver Activation Cmd: "modprobe snd_emu10k1"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)
alan@alan-OEM:~$ 

```

If anyone have any idea... please share :(

---

