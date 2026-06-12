---
title: "Touchpad problem - HP Pavilon dv6700"
date: 2010-05-05
forum: Hardware
---

### Post by crjackson on 2010-05-05
If you are familiar with the above HP lappy, you will know that there is a disable button for the touchpad.  This thing is really needed with Ubuntu because it's almost impossible to get it adjusted correctly so that the cursor isn't jumping all over the place when typing.

PROBLEM: After disabling the touch pad you have to leave it that way, and use an external usb mouse.  If you attempt to re-enable by pressing the button, all clicking functions cease to work (even on the external mouse), and the keyboard becomes unresponsive.

The cursor will still track and move on the screen, but you can't click on anything.

Does anyone have a solution for this?  I have filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/576062") on launchpad.

---

### Post by lidex on 2010-05-05
Not personally, but this guy seems to have a few:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing")

---

### Post by crjackson on 2010-05-06
> **lidex said:**
> Not personally, but this guy seems to have a few:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing")

Thanks, I didn't see anything that applies, but I'll search through it later today.

---

### Post by crjackson on 2010-05-14
I'm still having no luck with this.  Could someone please confirm the [[SIZE="3"][COLOR="Red"]**bug report**[/COLOR][/SIZE]]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/576062") so the devs will have a look at it?

---

### Post by Flash__Gordon on 2010-05-21
I too have the same issue with HP pavilion dv6000 series laptop. I have a work around that works. After turning back on and can't click (you may also notice that you can't type letters either) press Ctrl+Alt+F2 then Ctrl+Alt+F7 and you should be able to use external mouse and keyboard. Sometimes the touchpad will also begin working. I installed "pointing devices" from the software center and this seems to be working, however I only did this today and it is too soon to say conclusively. Hope this helps you somewhat. 

Flash_Gordon

---

### Post by lidex on 2010-05-21
No help with GSynaptics? Try gpointing-device-settings.

---

### Post by crjackson on 2010-05-21
> **lidex said:**
> No help with GSynaptics? Try gpointing-device-settings.

Thanks, I'll look into this.

---

### Post by wwuster on 2010-05-30
Did you ever find a solution for this? I just ran into it today after putting 10.04 on the same kind of laptop.

William

---

### Post by crjackson on 2010-05-31
Not really.  I'm out of town right now, but I plan to try a few things when I return.

---

### Post by Flash__Gordon on 2010-05-31
> **wwuster said:**
> Did you ever find a solution for this? I just ran into it today after putting 10.04 on the same kind of laptop.

William

No I still have the issue. It seems to have been reduced from not working to only failing after using the touchpad "off" button. Then loose keyboard and touchpad until ctrl+alt+f1 (or f2) and then ctrl+alt+f7 and keyboard will function again. (sometimes touchpad will also work but mostly just keyboard). I can always use usb wireless mouse though.

---

### Post by luigi_mb on 2010-06-01
> **Flash__Gordon said:**
> No I still have the issue. It seems to have been reduced from not working to only failing after using the touchpad "off" button. Then loose keyboard and touchpad until ctrl+alt+f1 (or f2) and then ctrl+alt+f7 and keyboard will function again. (sometimes touchpad will also work but mostly just keyboard). I can always use usb wireless mouse though.

On my HP dv7t the problem disappeared when I noticed that the NumLock light was on and I turned NumLock off.


/luigi

---

### Post by doans on 2010-06-02
I have the same problem on my HP dv6 series laptop. Very frustrating when using Lucid. Other than this problem Lucid runs very smooth on this laptop.

---

### Post by Professor IllDog43 on 2010-06-11
This might help you [http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/](http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/)

---

### Post by crjackson on 2010-06-13
so far I haven't found a solution on my lappy.  I hate it.

---

