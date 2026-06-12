---
title: "No sound SoundBlaster PCI128"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by morehouse on 2005-07-30
Hi guys!

Hei, I'm in troubles... I installed Ubuntu to a friend. I installed the codecs and everything as in ubuntuguide. Only difference: I installed totem-xine. Anyway everything went smoothly but I had this problem: I have no sound from mplayer and totem starting inside/from firefox.  :-# 

I have a Sound Blaster Audio PCI 128.

I tried to uncheck the sound_esd from the gnome configuration editor, with no results, actually doing this was worse; no sound at all.  :???: 

Is it related with multiple sounds - alsa & esd?

Any suggestion would be very welcome...

Thanks a lot,
  Antonio

---

### Post by varunus on 2005-07-31
Well, you should install libesd-alsa0 from synaptic first of all.  That way, ESD will use ALSA for output.

Try the following in a terminal:
```
sudo ln -s libesd.so.0 libesd.so.1
```

Does this fix your sound problem?

---

### Post by morehouse on 2005-07-31
Hi no it did not work.

By looking at lspci I get:

0000:00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 13)
0000:00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:04.4 Non-VGA unclassified device: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0b.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

And you can see I have two multimedia audio controller. When I use alsamixer, it looks like alsa changes the Inc CM8738 instead of Ensoniq 5880 AudioPCI.

Maybe I should uninstall alsa and compile alsa again.

Any idea?

---

### Post by mo_x on 2005-07-31
The c-media is probably onboard sound on your motherboard. Maybe you can disable it through the BIOS settings.

---

### Post by morehouse on 2005-07-31
Hei, I have audio finally.  \\:D/ 

Well, what I did is very simple...

Since I did not find an easy way to exclude the audio card embedded in the mother board from BIOS then I just connected the speakers to the output of the audio card of the ASUS motherboard. 

Now the sound works great, therefore I think I'll stick to it.

Thanks anyway for your help!

-- Antonio

---

### Post by varunus on 2005-08-02
Ahh, you have 2 sound cards.  That makes things different.  Here's how to get sound out of the sound blaster (you have to set up an asound.conf file as per this howto):
[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

---

