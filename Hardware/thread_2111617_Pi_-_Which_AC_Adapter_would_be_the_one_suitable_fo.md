---
title: "Pi - Which AC Adapter would be the one suitable for me"
date: 2013-02-02
forum: Hardware
---

### Post by ivotkl on 2013-02-02
So I've made up my mind and decided to build a Raspberry Pi home office station / media server (which will not be "open" 24/7, but I'm sort of a "green" guy... so it will help quite a lot)

I'm planning to get one of these "toys" but I'm unsure which AC adapter to buy. I live in Argentina and usual power output is 220~240 V and around 50-60Hz I believe. Will the Universal one work? I'm not sure the Amperes that come out of the socket.

It's description, as follows:
"Universal Mains 5V @ 2A power supply with integral 1.5m cable and microUSB plug. Interchangeable plug heads for UK, Europe, USA, Japan and Australia. Suitable for Raspberry Pi Model A or B."

"Micro USB UK power supply for Raspberry Pi"

Apparently, UK has the same power output (220~245) as we do here in Argentina and I have 3 pins sockets. Could you confirm? I don't want to burn my newly delivered Pi when the time comes. =P

My order, besides 512 MB B Type board, will include:

Raspberry Pi Type B Case - Clear
HDMI cable for Raspberry Pi
Ethernet network cable for Raspberry Pi
SD Card (pending)

Might buy an SD card at local store instead as I would like to get one bigger than 4 GB just in case. Will any SD Flash or Micro SD with SD adapter work? I'll probably get a Sandisk branded one.

Will any linux distro work in it? I'm planning maybe trying Damn Small Linux as Pi will be mainly intended for storing files and playing 720p/1020p videos.

Thank you in advanced.

**PS:** Will there be any Pi model with RAM slots?

**Edit:** I forgot to take in basic physics, so disregard the "I don't know current" part as Power equals Current multiplied by Voltage.

---

### Post by The Cog on 2013-02-02
> **ivotkl said:**
> So I've made up my mind and decided to build a Raspberry Pi home office station / media server (which will not be "open" 24/7, but I'm sort of a "green" guy... so it will help quite a lot)

I'm planning to get one of these "toys" but I'm unsure which AC adapter to buy. I live in Argentina and usual power output is 220~240 V and around 50-60Hz I believe. Will the Universal one work? I'm not sure the Amperes that come out of the socket.

It's description, as follows:
"Universal Mains 5V @ 2A power supply with integral 1.5m cable and microUSB plug. Interchangeable plug heads for UK, Europe, USA, Japan and Australia. Suitable for Raspberry Pi Model A or B."Sweet.> 
"Micro USB UK power supply for Raspberry Pi"

Apparently, UK has the same power output (220~245) as we do here in Argentina and I have 3 pins sockets. Could you confirm? I don't want to burn my newly delivered Pi when the time comes. =P

UK is nominally 230v, but US is 120v so that supply is truly universal. Your main issue is whether any of the interchangeable heads will fit Argentinian sockets, and I have no idea. 2A should be enough for the Pi, this page says they need 0.7A: [http://www.raspberrypi.org/archives/260](http://www.raspberrypi.org/archives/260)
> 
My order, besides 512 MB B Type board, will include:

Raspberry Pi Type B Case - Clear
HDMI cable for Raspberry Pi
Ethernet network cable for Raspberry Pi
SD Card (pending)

Might buy an SD card at local store instead as I would like to get one bigger than 4 GB just in case. Will any SD Flash or Micro SD with SD adapter work? I'll probably get a Sandisk branded one.
Any SD or micro-sd with adapter should work. I would suggest looking for a reasonably fast one. My Pi is running on a class 4 card and it's a little slow on "disk" access at times.
> 
Will any linux distro work in it? I'm planning maybe trying Damn Small Linux as Pi will be mainly intended for storing files and playing 720p/1020p videos.
Probably not. I think you need to look out for a distro made specially for the Pi because of the CPU and hardware. I've only ever tried the official Debian based one.

You may need to tinker with /boot/config.txt in order to get sound working through hdmi. I find even with my fiddled config.txt (below) that I need to boot the Pi with the hdmi connected in order to get the sound and the right picture size.

My /boot/config.txt:
```
# uncomment if you get no picture on HDMI for a default "safe" mode
#hdmi_safe=1

# uncomment this if your display has a black border of unused pixels visible
# and your display can output without overscan
#disable_overscan=1

# uncomment the following to adjust overscan. Use positive numbers if console
# goes off screen, and negative if there is too much border
overscan_left=-10
overscan_right=-10

# uncomment to force a console size. By default it will be display's size minus
# overscan.
#framebuffer_width=1280
#framebuffer_height=720

# uncomment if hdmi display is not detected and composite is being output
hdmi_force_hotplug=1

# uncomment to force a specific HDMI mode (this will force VGA)
hdmi_group=1
#hdmi_mode=1
#  19=720p, 31=1080p
hdmi_mode=31

# uncomment to force a HDMI mode rather than DVI. This can make audio work in
# DMT (computer monitor) modes
#hdmi_drive=2

# uncomment to increase signal to HDMI, if you have interference, blanking, or
# no display
#config_hdmi_boost=4

# uncomment for composite PAL
sdtv_mode=2

#uncomment to overclock the arm. 700 MHz is the default.
#arm_freq=800

# for more options see http://elinux.org/RPi_config.txt
gpu_mem=128

```

---

### Post by ivotkl on 2013-02-02
Dear Mr. Cog,
Thank you sooooooooo much for the prompt reply. I'll check it later and edit post if needed. Take care. =)

**Edit:** I've seen on Pi's site they sell Class 6 SD Cards and [this one](http://www.sandisk.com/products/memory-cards/sd/extremepro-sdxc-sdhc-uhs-1-95mbs/?capacity=64GB) from SanDisk is Class 10. Any compatibility issues known? Although, I would not know if I could get it in Argentina.

---

