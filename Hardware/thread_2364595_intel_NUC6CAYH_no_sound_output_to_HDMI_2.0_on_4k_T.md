---
title: "intel NUC6CAYH no sound output to HDMI 2.0 on 4k Television"
date: 2017-06-25
forum: Hardware
---

### Post by kutabid on 2017-06-25
Affected : intel NUC6CAYH

Expected behavior :
HDMI audio output to 4k TV via HDMI 2.0 port.

Observed behavior :
Xubuntu 17.04 (Kernel 4.10x) : **No HDMI audio** at any resolution. Sound works through Ear phone jack.&#8203;
Librelec 8.02 : **No HDMI audio** at any resolution.&#8203; Sound works through Ear phone jack.
Windows 10 (+/-Kodi 17.3) :** No HDMI audio** output at all resolutions.&#8203; Sound works through Ear phone jack.&#8203;

Actions :
Checked BIOS sound is 'ON' (it was).
Updated BIOS to latest AYAPLCEL.86A.0038 ([http://intel.ly/2t4MscK](http://intel.ly/2t4MscK))
Updated Megachip HDMI Firmware to 1.66 via Windows only software ([http://intel.ly/2tI9kwH](http://intel.ly/2tI9kwH))

Repeat test observed behavior:
Xubuntu 17.04 (Kernel 4.10x) : **No HDMI audio** at any resolution. Sound works through Ear phone jack.&#8203;
Librelec 8.02 :** No HDMI audio** at any resolution.&#8203; Sound works through Ear phone jack.&#8203;
Windows 10 (+/-Kodi 17.3) &#8203;: ***HDMI audio output as expected*** at all resolutions.&#8203; Sound works through Ear phone jack.&#8203;

Reference:
MCDP28x0 DisplayPort1.2a-to-HDMI 2.0 Converter
[http://www.megachips.com/products/displayport/MCDP28x0](http://www.megachips.com/products/displayport/MCDP28x0)
NUC6CAYH Product Change – Up-to-date Firmware Out of the Box
[http://nucblog.net/2017/04/nuc6cayh-product-change-up-to-date-firmware-out-of-the-box/](http://nucblog.net/2017/04/nuc6cayh-product-change-up-to-date-firmware-out-of-the-box/)
[https://qdms.intel.com/dm/i.aspx/CA589152-F553-41FA-99A6-592E3796B9C8/PCN115449-00.pdf](https://qdms.intel.com/dm/i.aspx/CA589152-F553-41FA-99A6-592E3796B9C8/PCN115449-00.pdf)

Filed a bug at Linux DRI, sourly informed 'it works for everybody'.

Clearly it doesn't...
&#8203;Suggestions?

---

### Post by kutabid on 2017-06-27
dmesg output

[https://paste.ubuntu.com/24962082/](https://paste.ubuntu.com/24962082/)

alsa info

[https://paste.ubuntu.com/24962089/](https://paste.ubuntu.com/24962089/)

kodi log

[https://paste.ubuntu.com/24962092/](https://paste.ubuntu.com/24962092/)

---

### Post by CatKiller on 2017-06-27
ALSA says that it's found a HDMI output, so that part's working OK.

Kodi says that your default audio device is headphones, which is why Kodi isn't putting sound out through HDMI.

You can change the selected device with the volume control on the desktop. You can change the default device with pavucontrol. You can change the device that Kodi uses from the default within Kodi.

I recently got a NUC (the NUC7i5BNK in my case) and it wouldn't put out audio over HDMI, regardless of the BIOS setting, until I'd updated the BIOS. Then I needed to change the device that PulseAudio uses, and the device that Kodi uses, and then turn up the volume when media was actually playing. It works fine now.

My experience of both NUCs and Kodi is only 3 days long, though.

---

### Post by kutabid on 2017-07-13
Thanks CatKiller.
This model has a weird converter chip (LSPCON).
It does'nt work at all until both the motherboard firmware & the LSPCON firmware are updated.
The LSPCON updater software is .. wait for it.. Windoze only.
After all the rigamarole of obtaining & installing an evaluation version of Windoze & running the Windoze only firmare updaters I find the hardware works perfectly in Windoze & really flakey (if at all) under Linux.
Best solution in Linux is run a bleeding edge distro or manually update Xorg & ALSA to very latest stable versions. Even then sound via HDMI is very flakey (works for some app's not others, requires log out/in to resore sound when it dies mysteriously).

intel refuse to provide meaningful support.
Bugs filed go unactioned.

Essentially many of these NUC models are WIndoze only.
Its too much of an expensive guessing game for me, I'll ebay it off to a Windoze lemming & never buy a NUC again.

---

### Post by CatKiller on 2017-07-13
I'm sorry to hear that.

My NUC has been fine with Ubuntu 16.04 once I updated its firmware; it runs Kodi controlled through the TV remote and Steam BPM with the Steam controller, and is also running two Minecraft servers and a Windward server. They definitely aren't all bad.

Although I'm not using HDMI 2.0. That might be relevant. ISTR that there was some announcement about a problem with HDMI 2.0 when I was getting the firmware. My telly isn't that new, so I didn't look into it closely. (EDIT: Ah, I see that you said that you did that already)

---

