---
title: "TV out with Radeon driver and R600 card"
date: 2011-05-06
forum: Hardware
---

### Post by qrazi on 2011-05-06
I have Googled now for a few days, but I cannot get the S-video on my mainboard to display anything on the screen of my CRT tv.

My mainboard is an Asus M2A-VM HDMI, which uses the AMD 690G chipset with integrated Radeon X1250 videocard.

[These suggestions]("https://wiki.archlinux.org/index.php/ATI#TV_out") didn't work for.

I get the following error:
> qrazi@mythbuntu:~$ xrandr --output S-video --set load_detection 1
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  31
  Current serial number in output stream:  31

When I just force a mode on the S-video, the tv screen shows a very garbled image, whilst the monitor just stops working.

I'm pretty sure I'm not the only one with this problem, but I haven't found a solution up till now.

Any suggestions?

---

