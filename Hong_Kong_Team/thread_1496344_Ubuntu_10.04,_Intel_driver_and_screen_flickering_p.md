---
title: "Ubuntu 10.04, Intel driver and screen flickering problem"
date: 2010-05-29
forum: Hong Kong Team
---

### Post by abgalphabet on 2010-05-29
I've installed the Ubuntu 10.04 on my fujitsu notebook for a month. I found that it sometimes flickering (whole screen in white and then back to normal) the whole screen. Does anyone have the s ame problem?

My notebook is Fujitsu S6430 with Intel Graphic 4500.

---

### Post by omaralqady on 2010-05-29
I have the same issue with a Fujitsu Siemens Li3710, and Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller. Any help would be appreciated :)

---

### Post by duke.tim on 2010-06-06
I have a similar problem on my hp dv6. an intermittent screen flicker.

---

### Post by Sylslay on 2010-06-09
I have FS aswell.

And Ubuntu 10.04 sine 29 april
Today found that add this to grub command line

i915.modeset=1 gfxpayload=1024x768

help much to avoid flickerig screen before load gnome.

PS.But installed intel ppa drivers and can get only vesa drivres insted intel. :lolflag: Overall preformacne is worse
Now tray downgrade or switch to intel drivers

---

### Post by Whisp3r on 2010-06-15
I am still having problems, despite all of the solutions offered (GRUB menu, xorg updates, etc). This is going to be a killer for me for Ubuntu - I cannot work on a computer with flickering at random times. It gives me a headache, and I can't give presentations. Hopefully someone figures this out soon.

---

### Post by samiux on 2010-06-26
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Screen_Keeps_Flickering](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Screen_Keeps_Flickering)

Hope this may help.

---

### Post by omaralqady on 2010-06-26
This is the output of 'sudo lspci':
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

I think my graphics card is either 00:02.0 or 00:02.1, is that right? If it is, then there is no solution for me on the link you provided, if it's not how can I find out what it is? 

Thanks :)

---

### Post by Michaelsheldon on 2010-08-15
I had the same problem running my Acer 7730z with an nvidia card.

I tried this

[http://jimmod.com/blog/2010/06/solving-fixing-ubuntu-10-04-lucid-screen-flickerdistortion/](http://jimmod.com/blog/2010/06/solving-fixing-ubuntu-10-04-lucid-screen-flickerdistortion/)

So far (been about 4 days) its not had any flickering in the slightest.

Hope that's of some use to you all.

---

### Post by witeshark17 on 2010-08-15
If you have more input or pics (I know, not likely) here's [ a LaunchPad](https://bugs.launchpad.net/ubuntu/+bug/587935) thread

---

