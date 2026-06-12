---
title: "Almost none of my hardware is recognized!"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by tyrannicalpolitics on 2005-04-15
Almost none of my hardware is recognized when using Kubuntu. I have a Dell dimension 2400 (piece of shite) with an onboard Intel Graphics controller. I've noticed that even after **hours** of tinkering I am still getting very little results. I can't get online through dialup because my modem is not recognized. Also I can't play music in Amorak. I get the following error:

Sound Server Informational Message:

error while initializing the sound driver:

Device: default can't be opened for playback (device or resource busy)

The server will continue using the null output device.

Most annoyingly of all I can only access my windows files from my other hardrive by running Konqueror in root mode. Either that or editing in root mode. Can I change this setup in the Kommand screen? I can't open a lot of file types and many are unsupported.  Furthermore I can't put anything on this hardrive using Kubuntu because my cd-roms are not recognized. I am very new to Kubuntu and I'm learning pretty fast, but I'm annoyed that they made setup such a pain in the ass. Is there anywhere I can download packages or patches to make things easier? Any tips or links would be **very** much appreciated. Thanks.

Cheers

---

### Post by accuser on 2005-04-15
> I can't get online through dialup because my modem is not recognized.
Most likely this is a WinModem, which means that it is a bit of hardware for driving the telephone line, with most of the work being done by your CPU. It is possible to get these working with Linux, but you will need to do some leg work. Find out the make/model of your modem, and google for information about using it with Linux.

> Most annoyingly of all I can only access my windows files from my other hardrive by running Konqueror in root mode.
This is actually for security. You need to make changes to the /etc/fstab file which records details of the drives and partitions normally available to the operating system. Take a look at the manual for fstab:
```
$ man fstab
```
For mount options, take a look at the manual for mount:
```
$ man mount
```

> I can't open a lot of file types and many are unsupported.
This is because you won't have equivalent software installed for Linux to handle these Windows file types, or you haven't downloaded codecs for audio/video streams.

Your best bet is to take time to read through the [Unofficial Ububtu Guide](http://www.ubuntuguide.org) for help getting set up.

It can be frustrating going from Windows to Linux if not everything works first time, but let me reassure you that the journey is worth it. ;-)

---

### Post by tyrannicalpolitics on 2005-04-15
Accuser,

Thank you :). Although I must say that I knew most of what you told me I didn't really know much about fstab. I'll try everything you said and hopefully it will work out eventually. I guess getting online is the most vital thing I can do. Do you know anything about the universe repository? Thank you and Take care

-b-

---

### Post by tyrannicalpolitics on 2005-04-15
Accuser,

Actually my modem is an Intel(R) 537EP V9x PCI modem

Right now I'm getting a redhat precompiled driver for it that I will change into debian if possible. If not I have already downloaded a general uncompiled driver for Linux. Hopefully I will get faster internet soon anyway so I can download more of the linux drivers and applications! :wink: Once I'm down downloading things that I need I'm going to go in Linux again and work for a bit. I'll post any new developments.

Peace

-b-

---

### Post by tyrannicalpolitics on 2005-04-15
Yep. It is most definately a *beep* winmodem. Great news for me. ](*,)

---

