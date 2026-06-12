---
title: "HDMI Input on Alienware M18x"
date: 2011-12-11
forum: Hardware
---

### Post by stanjr on 2011-12-11
I have an Alienware M18x laptop that has an HDMI input.  I dual boot between Win7 64-bit and Ubuntu 11.10 64-bit.  When I am in Win7, the HDMI input works fine for both audio and video when I plug my PS3 in to play it on the laptop's monitor; however, when I am in Ubuntu, only the PS3 video comes through without any audio.

I can't seem to find any answers searching throughout the Internet.  Can anyone help me figure out why the audio won't come through when I use Ubuntu?

Thanks!

---

### Post by papibe on 2011-12-11
Hi stanjr. HDMI input on a laptop? That's really cool!

This is what I do: First I would check if the device is being recognized as an input device:
```
arecord -L
```
Then, I would check if the input is muted using alsamixer:
```
alsamixer
```
Remember to press F4 to see the input (capture devices).

After that I would select the input device on 'Sound Properties' before connecting your PS3 (like you would do if you had several mics and wanted to record from one of them).

Hope it helps, and let us know hot it goes.
Regard.

---

### Post by stanjr on 2011-12-11
```
stanjr@stanjr-alien-ubuntu:~$ arecord -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=PCH,DEV=0
    HDA Intel PCH, STAC92xx Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, STAC92xx Analog
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, STAC92xx Analog
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, STAC92xx Analog
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, STAC92xx Analog
    Hardware device with all software conversions
```

Nothing is muted in alsamixer.

The only type of audio inputs I have listed under Sound Settings are:
Analog Microphone
Internal Microphone
Analog Line In

It doesn't seem that an HDMI inupt is noticed at all there.

---

### Post by papibe on 2011-12-11
Yes. It looks like the device is not visible.

Could you post the result of these commands?
```
lspci | grep -i vga

sudo lshw -C display

```
Regards.

---

### Post by stanjr on 2011-12-11
Thanks for your help in this!  Here are the outputs to the two commands:

```
stanjr@stanjr-alien-ubuntu:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation Device 1251 (rev a1)
```

```
stanjr@stanjr-alien-ubuntu:~$ sudo lshw -C display
[sudo] password for stanjr: 
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:cc000000-cdffffff memory:c0000000-c7ffffff memory:c8000000-cbffffff ioport:7000(size=128) memory:ce080000-ce0fffff
```

---

### Post by QuantumWarlock on 2011-12-16
Hello,
 
I have been trying versions of ubuntu including 11.10 64 and 32-bit on my M18x. It hangs every time. I have also tried wubi as well as dual-boot. You seem to have gotten ubuntu to work? What might I be doing wrong?

---

### Post by stanjr on 2011-12-16
I originally had the fresh install of Win7 64-bit installed on it (as it came), then installed a fresh install of Ubuntu 11.10 64-bit for a dual-boot situation with grub2.  Everything seems to work fine (except, of course, the hdmi input audio).  I don't know what might be going wrong :(

---

### Post by Mryusef1 on 2012-02-29
does anyone know of an HDMI input card that I can use to watch tv in Ubuntu 11.10 from my AT&T Uverse box?

---

