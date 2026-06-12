---
title: "some USB devices are not detected"
date: 2016-09-10
forum: Hardware
---

### Post by VictorR on 2016-09-10
There were no problems for years with Pnp USB devices, until after some updates - I suspect it was LTS 14.04.1 to 14.04.2 switch (I can be mistaken), some USB devices are no longer detected when hot-plugged. I mean, **lsusb** does not show any new devices and
dmesg | grep -i usb
does not show any activity when run before and after the device was connected.

Affected computers: lubuntu 14.04 LTS on old EEE PC 4G; two desktops running Linux Mint 18 and 17.3.

Affected devices: HD action camera, smart watch (a phone in fact), Chinese Android A1200 mobile phone and now Sony-Ericsson XPERIA mobile phone also running Android.
Not affected devices: Canon D20 camera, FujiFilm digital camera, keyboards, SD card reader, WIFI dongle, wireless mouse.

All affected devices show that they were connected to a charger, which is a computer in fact, but no options to select the kind of connection. The computer does not react to connection at all.

All affected devices can be connected without problems to a Windows computer; and I had no problems with them about half year ago on all computers listed above.
It looks like a kernel regression for me. As I said, there no records in any log, when the device is connected, so I just don't know where to look.
~$ uname --all (for all computers listed above)

Linux kodi2 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:02 UTC 2015 i868 i868 i868 GNU/Linux

Linux main 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Linux Louisa 3.19.0-66-generic #74~14.04.1-Ubuntu SMP Tue Jul 19 19:56:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Any help would be greatly appreciated. Maybe I should change some BIOS setting to match new kernels.

**Edit:**
The problem was **in the cable**. I broke one cable and replaced it another one (type micro-B). it happened that I got three nice looking cables with USB chargers; apparently they don't have data wires. I was stupid enough not to check everything with same conditions. At home I usually used one of the charger cables, at work it was a cable from my bag which worked perfectly with the Windows machine. When I collected all available cables at home and tested all of them, two proper ones happened to be permanently connected to charges (because they are long) and three wrong ones I wanted to send data through. Digital cameras use different cables with thicker connectors (mini-B).

---

### Post by sudodus on 2016-09-10
There might some old files that do not work with some new files, and it started after that particular update. In that case a clean new system should work.

My devices work, also an android phone (Samsung), in my Lubuntu + Xubuntu 16.04.1 LTS combo system. The kernel is 4.4.0-36

```
$ uname -a
Linux xenial32 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:00:59 UTC 2016 i686 i686 i686 GNU/Linux
```

I suggest that you try in live systems booted from the iso files of

[LIST]
[*]16.04.1 LTS
[*]Xenial daily
[*]Yakkety daily[/LIST]

You can find the daily iso files via this link: [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

---

### Post by VictorR on 2016-09-10
Thank you for your reply. I followed your suggestion and although it did not solve the problem, it forced me to think about it a little bit more and find the reason. Thanks!

---

