---
title: "copier machine scanners not detected for A3 ADF auto document feeder"
date: 2020-10-01
forum: Hardware
---

### Post by anonononono on 2020-10-01
Hello,

I'm trying to use ADF auto document feeder for A3 sheets and have tested a few copier machines on Kubuntu20.04, 4 different, all failed.

One isn't recognized at all when I wire it via USB and/or ethernet - the xerox workcenter 7220. However tbh I just tried the driver that the ubuntu printers window proposed me, namely nothing, and didn't try any manufacturer driver, assuming such exist. Correct me if I'm wrong but AFAIK we just need to put manufacturer .ppd into /etc/cups and then browse it manually when in the printers configuration GUI of ubuntu, right?

The 3 others are :
- a konica bizhub C__4, with driver Konica Minolta C554SeriesPS : recognized + prints.
- a samsung multi xpress X 4300 LX, with Samsung X 4300 Series PS : recognized but unfortunately I didn't try to print
- sharp mx 2314N, with sharp mx 2314N PS 1.0 : recognized but unfortunately I didn't try to print

My issue is that none of these copier machine scanners are detected when launching either simple-scan / xsane / skanlite / gscan2pdf  !

Even though when USB wiring my little modest HP deskjet (ink) 2510 it works like a charm and I'm able to launch every one of these GUI.
[https://www.openprinting.org/printer/Samsung/Samsung-X4300https://www.openprinting.org/printer/Samsung/Samsung-X4300](https://www.openprinting.org/printer/Samsung/Samsung-X4300https://www.openprinting.org/printer/Samsung/Samsung-X4300) says that the samsung one should work flawlessly but it apparently doesn't.
Also I tried official OEM drivers from konica and samsung, that mention explitly "Linux"...
Also I already sudo apt install libsane-dev libsane-common sane-utils

In addition, when trying those printers while being LAN wired to them, I used to frequently get the KDE pop-up that says :
Wired Interface (eno1)
IP configuration was unavailable

1) In the end does anyone already manage to USB scan on linux via enterprise copier machines? Do you remember the models?
2) Is it really possible on linux to do SMB scan-to-folder by triggering a copier button to send documents on a linux folder, without passing through a windows server + samba ? No matter if the answer is yes or no, do you know some tutorial?
3) Does "working perfectly" on a printer dedicated page on openprinting.org means that both printer and scanner will work perfectly, or does it actually just speak for the printer side ?

By thanking you in advance

---

