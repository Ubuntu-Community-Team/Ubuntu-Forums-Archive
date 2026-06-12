---
title: "[AMD/ATi] HDMI sound not working  - graphics driver not working"
date: 2013-08-05
forum: Hardware
---

### Post by peter16 on 2013-08-05
Hello!

I have the following problems:


[LIST=1]
[*]The sound doesn't work on my TV (HDMI).
[*]AMD drivers didn't work - I couldn't open up the catalyst control center once the driver was (incorrectly) installed, and when I tried some legacy driver after some googling, I could only log in through the command prompt. I had to re-install Ubuntu.
[*]The Additional Drivers window is completely blank.
[/LIST]

I don't really need the proprietary as long as I can play 1080p movies, watch those movies on my TV with sound and play WoW (I had some problems with Windows, and I can't find a bigger USB, so it is what it is).

Is there a way to fix this?

Thanks in advance.

---

### Post by TheFu on 2013-08-05
I believe that for audio to work over HDMI, you **must** load the proprietary ATI drivers.
I find that after every new kernel install, I have to reload the ATI drivers again.  No need to purge first, just force a --reinstall.
This happens often enough, that I have a script to do it on my XBMC box.
```

sudo apt-get  --reinstall install fglrx
 export DISPLAY=:0
 fglrxinfo 
 aplay -l
```

The last command helps me validate the correct audio drivers are working. If not, might need to reboot.

---

### Post by peter16 on 2013-08-05
Thank you for your help, TheFu.

I got the audio working by adding this to */etc/default/grub*:
> GRUB_CMDLINE_LINUX="radeon.audio=1"

I'll wait with the proprietary drivers for now; I'm going to see how well the open source drivers handle HD movies and World of Warcraft.

---

### Post by Mark Phelps on 2013-08-06
There may simply not be any proprietary drivers available anymore for your AMD/ATI chipset.  Open a terminal, enter "lspci" and look for the line containing "VGA".  Post the results back here.

---

### Post by peter16 on 2013-08-10
Thank you for the response, and sorry for the delay.

```
$ lspci | grep VGA
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV730 PRO [Radeon HD 4650]
```

I've used AMD drivers on Linux before, but that was months ago.

---

### Post by Yellow Pasque on 2013-08-10
> **TheFu said:**
> I believe that for audio to work over HDMI, you **must** load the proprietary ATI drivers.
False. See: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

---

### Post by Yellow Pasque on 2013-08-10
> I don't really need the proprietary as long as I can play 1080p movies
Unfortunately, open-source video playback accel isn't working on some older AMD cards, and the 4650 is one of them. 
If I was you, I would try making a separate install of Ubuntu 12.04.1, the proprietary legacy driver, and using this trick: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Using_XBMC_player_.28XvBA.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Using_XBMC_player_.28XvBA.29)
If you like how that works, you can make it your main install.

---

### Post by peter16 on 2013-08-10
Thank you for your response.

> **Temüjin said:**
> Unfortunately, open-source video playback accel isn't working on some older AMD cards, and the 4650 is one of them.

But it should work with the proprietary driver from AMD? I just don't understand why it doesn't work to install it.

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)


> **Temüjin said:**
> 
If I was you, I would try making a separate install of Ubuntu 12.04.1, the proprietary legacy driver, and using this trick: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Using_XBMC_player_.28XvBA.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Using_XBMC_player_.28XvBA.29)
If you like how that works, you can make it your main install.

So I would still have to use XBMC, even when using the driver from AMD?

---

### Post by Yellow Pasque on 2013-08-10
The legacy driver only works older Xservers, so you have to use Ubuntu 12.04.1 if you want to use that.

XBMC is the only app I know of that supports xvba (the method used by the proprietary driver) in Linux. You could also try the other method listed on that page and use VA-API-enabled players (VLC, for example). [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Using_the_xvba-va_Driver_.28VA-API.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Using_the_xvba-va_Driver_.28VA-API.29)

---

