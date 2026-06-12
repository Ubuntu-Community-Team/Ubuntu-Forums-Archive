---
title: "Sound on Acer Aspire 6935G"
date: 2009-04-27
forum: Hardware
---

### Post by applefreakpeeps on 2009-04-27
Hi,
         I am using Ubuntu 9.04 Jaunty Jackalope with the latest alsa-driver snapshot. The sound system does not work without a hda-verb command manually executed every time the system starts up. The command I execute is:

hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2

If I do this I get audio out. But my internal mic does not work and nor does jack sensing. When I insert a device into the headphone jack the speakers do not get muted and there is also no sound from the headphones themselves. Even an external mic/line-in device does not work. I have attached the output of alsa-info.sh here as a zipped archive.. Please go through it and try to see what the problem could be... I had posted this on alsa-devel mailing list but no response so far..

Toggling the headphone jack in the mixer turns the internal subwoofer on/off.. so I think it's a switch mapping problem..

Note: setting model=acer, acer-aspire or auto in alsa-base.conf makes no difference at all.

Please help.

Thanks and Regards,
Karthik

---

### Post by applefreakpeeps on 2009-05-07
help???

---

### Post by 1roxtar on 2009-05-07
Try this and see if it works...


1. Open up the volume control.

2. Go to Edit.

3. Go to Preferences.

4. Scroll down list to External Amplifier. (check it)

5. Once it is check - close that out.

6. Go back to the volume control panel.

7. You should now see a Switches TAB at top. (select it)

8. Search for the External Amplifier on the list you see.

9. Uncheck the External Amplifier.

10. Now close out and go test your sound. 

:popcorn:

---

### Post by applefreakpeeps on 2009-05-14
No effect.. jus managed to get headphone (line-out) volume by unmuting the surround control in the mixer.. NO input devices work yet..

---

