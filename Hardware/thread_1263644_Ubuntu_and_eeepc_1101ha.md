---
title: "Ubuntu and eeepc 1101ha"
date: 2009-09-11
forum: Hardware
---

### Post by raminaghrobis on 2009-09-11
Hi, I've had a few issues with ubuntu 9.04 and my eeepc, mainly to do with drivers. Wired and wireless networks both didn't work (although wired's fine now - here's the thread [http://ubuntuforums.org/showthread.php?t=1230045&highlight=eeepc](http://ubuntuforums.org/showthread.php?t=1230045&highlight=eeepc)) and I also have no sound.

Does anybody know which driver is needed for the sound card?

Thanks in advance!

---

### Post by Adavur on 2009-09-11
Hi.

I am going to buy this netbook today. I've read  a lot about the internet og graphic drivers, but not about the sound. I hope you find out something, and if you do, please post it here in the threat. Did you try to plugin ear phones?

Anyway, just wanted to hear how the bluetooth and the webcam works. And does the battery life last as long as in Windows?

---

### Post by raminaghrobis on 2009-09-11
Earphones don't work. I haven't tried the webcam but I assume it's the same. As for bluetooth I uninstalled it first thing so no idea...
I get about 7 hours battery with Xubuntu on power saving mode minus a few apps (like bluetooth), but then it should take a few cycles for the battery to be fully efficient, so battery life may yet go up.

Anyway good choice ^^

---

### Post by Spock112 on 2009-09-16
Hi,
I run the 1101HA with UNR 9.04.
Most things work just fine. But some of my Hotkeys don't work or do something else.
Does anyone else have this problem?

---

### Post by Chronon on 2009-09-16
@Spock112 eee-control allows you to remap some hotkeys to user defined actions, change performance profile, disable hardware when not in use (e.g. bluetooth, camera, WiFi, card reader).  I don't know if your model is supported yet or not.  Check it out here: [http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/)

@raminaghrobis That's too bad.  I have the 1000HEB and most things worked pretty well initially.  It looks like Spock112 is not having your issues, so it appears your hardware is supported, at least.  Just a guess but it sounds like you might be having some issues due to a different configuration (e.g. Xubuntu vs. UNR).

---

### Post by jbernardo on 2009-09-19
I am running kubuntu karmic lpia on mine. Brightness keys don't work, wifi/bluetooth key is only partially working (only wifi), the battery lasts 6-7 hours. The screen is "slow" (15-16 fps in glblur) but usable. Overclocking (even though enabled in the bios and working in XP with HybridEngine) doesn't work, and I have yet to find a app that will work in karmic/with the 1101ha.
But it is snappy to use, with screen effects disabled, the large screen is a joy to behold, the keyboard is ok, and the touchpad is nice, even if it does multitouch only in windows. I gave my AA1 to my wife (who always said she didn't want a netbook and is now enjoying it a lot), and am using this exclusively...

I forgot, sound mostly works well, but as some times alsa gives strange errors in dmesg and sound stays off, I installed the latest alsa code:
"sudo aptitude install module-assistant; sudo m-a update; sudo m-a prepare; sudo m-a a-i alsa"
Now the sound always works. I only have to do the last step for any new kernel.

---

### Post by raminaghrobis on 2009-09-19
But does anybody know what the sound card driver is and how to install it?

---

### Post by jbernardo on 2009-09-19
It's a intel hda MID, with a Realtek ALC269 chip. And to install it you don't have to do anything - the alsa auto-detect works. I just found the kernel alsa would sometimes fail to initialize properly the chip, so I installed the standalone version with module-assistant.

---

### Post by Spock112 on 2009-09-19
No, eee-controle does nothing (does not support the 1101ha) neither does eee-applet work ... and eeepc-acpi-scripts aren't installable on 9.04 ...

@Adavur: if you edit your /etc/hal/fdi/policy/shmconfig.fdi like this
```
 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>

```multitouch works.

So nobody else have the problem with the keys ... then it must have something to do with my German layout.

---

### Post by jbernardo on 2009-09-19
> **Spock112 said:**
> multitouch works.

Can you please run "synclient -m 100" in a terminal a tell me if the "f" column ever shows anything different from 0 or 1? it should show the number of fingers that press the touchpad, but on mine (running karmic lpia) it only shows 1 maximum, even with the exact same fdi file you posted. If it does show anything like 2 or 3, please tell me the version of your xserver-xorg-input-synaptics.

---

### Post by Spock112 on 2009-09-21
mm ... no ... the "f" collum shows at maximum 1 ...
but multitouch scrolling and right mouseklick (both 2 finger actions) work.

---

### Post by jbernardo on 2009-09-21
> **Spock112 said:**
> mm ... no ... the "f" collum shows at maximum 1 ...
but multitouch scrolling and right mouseklick (both 2 finger actions) work.

That only means you have the driver with the multi-touch emulation enabled... :(

---

### Post by raminaghrobis on 2009-10-07
@ jbernado How do you install the standalone version?

---

### Post by jbernardo on 2009-10-07
> **raminaghrobis said:**
> @ jbernado How do you install the standalone version?

You have to install module assistant first:
```
sudo aptitude install module-assistant
```
Then tell it to install alsa:
```

sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
```
Everytime you update the kernel, you should do these last three steps to get the latest alsa driver.

---

### Post by raminaghrobis on 2009-10-10
I tried what you suggested, and it still doesn't work. Could it be something else?

---

### Post by jbernardo on 2009-10-10
> **raminaghrobis said:**
> I tried what you suggested, and it still doesn't work. Could it be something else?
Could it be mixer settings? For the internal mic to work, I have to enable capture, and to reduce distortion I have to set capture volume at 50% approximately.

---

### Post by raminaghrobis on 2009-10-11
So simple...

I works fine, thanks a lot. (Although the volume's quite low, I'm assuming that its just the speakers that are lousy.)

---

### Post by asedas on 2009-11-05
I can't make "synclient -m 100" work. I always get "Can't access shared memory area. SHMConfig disabled?". wtf??

---

### Post by jbernardo on 2009-11-06
> **asedas said:**
> I can't make "synclient -m 100" work. I always get "Can't access shared memory area. SHMConfig disabled?". wtf??

Common problem - check on the community help, [here]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig").

---

