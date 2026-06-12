---
title: "Toshiba Satellite A200"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by rayle_terleir on 2008-03-31
Hello there Ubuntu forums,
You are currently reading the post of a desperate person. I have decided to finally install Ubuntu on my new laptop (Toshiba Satellite A200). I have fond memories of Ubuntu on my old A100, and I decided to test the newer release to see what has changed. I was disappointed to find 3 things:

1) My sound does not work. I have an ALC268 (ALSA) sound card, and I have had no sound whatsoever from this particular device. My ATI HD audio card (OSS) I have manage to jury rig using a fix from here to get sound in VLC media player, Totem and Amarok, but nothing else. I have tried every fix under the sun, installed so many different drivers, yet still nothing.

2) My wireless card does not work. I have a Realtek 8187b wireless card, and I have tried so many things to get it to detect my home network. So far, I have managed to install the Windows XP drivers with ndiswrapper, and now the card is detected, but it still won't connect  to my network. I have tried DHCP, ip4 and a static ip setup, yet still nothing.

3) Compiz fusion. I finally managed to install the proper video drivers for my ATI Radeon x1200 (which, by the way, does not appear on the ATI website nor the rest of the internet) using Envy. I tried to load Compiz effects, and much to my dismay, the effects worked, by my usable desktop shrunk to 2/3 normal size into the top left corner of my screen! I have a large empty area where I can see my wall paper, yet when I move my mouse cursor or anything over to it, it disappears!

I know from reading the forums that problems 1 and 2 are very common, but I am close to giving up. Ubuntu used to work so well for me, but now I am considering uninstalling it and formatting my laptop again. I'm begging you Ubuntu forums, help me. Any bug fixes which you know will help me on my way, please post. I want to keep my Ubuntu install, but it's just too much trouble at the moment.

Much appreciated guys.

---

### Post by bobnutfield on 2008-04-01
I can help you with the wireless problem.  I just purchased a Toshiba A210 and it has the same internal USB wireless Realtek 8187B.  There is no linux module for it yet (though there will be soon in an upcoming kernel).  For now, ndiswrapper is your only choice and I have it working well with it.  However, I noticed in your post that you used the WinXP driver in ndiswrapper.  That driver will not work.  You must use the Win98 driver.  Download them from Realteks site (you will find a download section to navigate to.  Downline the Win98/WinXP drivers .zip file.  Save it to your home directory, extract it and open the .inf file as text.  About a quarter of the way down, you will see and entry like this:

```
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
```

Add the following line:

```
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200
```

Save it, and then use that file to install to ndiswrapper.  As soon as you do:

ndiswrapper -l

you should see the driver is install and hardware is prensent.  Reboot and you should now have wlan0 available to you.

I also had trouble with sound in every distro I tried with this laptop, but finally found that Hardy Beta would do it (Gutsy would not.)

Hope this helps, it worked for me.

Bob

---

