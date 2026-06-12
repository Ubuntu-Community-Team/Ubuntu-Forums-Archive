---
title: "No sound from internal speakers on fresh installation, 2017 iMac"
date: 2023-03-29
forum: Hardware
---

### Post by jugglerdave on 2023-03-29
Hi all, I'm hoping somebody can provide advice.  I have a 2017 iMac and recently installed Ubuntu; everything seems to be working except the sound.  I get no sound from the internal speakers (they work fine in macOS 12 Monterey, that's what was installed when I got it).  Here's a hardware probe of the machine:

[https://linux-hardware.org/?probe=0805df69aa](https://linux-hardware.org/?probe=0805df69aa)

My limited searches have indicated this is a common problem with this all-in-one sound card and I haven't been able to find any solution.  

[FONT=Courier New]dave@dave-iMac:~$ inxi -SMA
System:
  Host: dave-iMac Kernel: 5.19.0-38-generic x86_64 bits: 64
    Desktop: GNOME 42.5 Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Apple product: iMac18,3 v: 1.0
    serial: <superuser required>
  Mobo: Apple model: Mac-BE088AF8C5EB4FA2 v: iMac18,3
    serial: <superuser required> UEFI: Apple v: 499.40.2.0.0 date: 08/22/2022
Audio:
  Device-1: Intel 100 Series/C230 Series Family HD Audio
    driver: snd_hda_intel
  Device-2: AMD Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
    driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.19.0-38-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes[/FONT]

I'd be grateful for any ideas.

---

