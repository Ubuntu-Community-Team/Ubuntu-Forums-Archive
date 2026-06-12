---
title: "usb bandwidth issue with edirol ua-25ex soundcard"
date: 2010-07-04
forum: Hardware
---

### Post by raboofje on 2010-07-04
I have a UA-25EX USB 1.1 sound card, which on another machine works fine at 44.1kHz, 48kHz (full duplex stereo), 96kHz (half duplex stereo).

On my new laptop, a Dell Latitude E6510, I'm running into trouble: it works at 48kHz half-duplex stereo, but not at 44.1kHz full-duplex stereo, or even 96kHz half-duplex. dmesg shows:

```
[ 4372.331943] cannot submit datapipe for urb 0, error -28: not enough bandwidth
```

The USB ports are connected to a EHCI Host Controller/hub shared by an internal bluetooth module and smartcard reader. 

Is there anything I can do to make this card work in full duplex again? Or is this a hardware issue?

---

### Post by lidex on 2010-07-06
I don't know, maybe specifying larger nrpacks. 

> Module snd-usb-audio
  --------------------

    Module for USB audio and USB MIDI devices.

    vid             - Vendor ID for the device (optional)
    pid             - Product ID for the device (optional)
    nrpacks	    - Max. number of packets per URB (default: 8)
    async_unlink    - Use async unlink mode (default: yes)
    device_setup    - Device specific magic number (optional)
                    - Influence depends on the device
                    - Default: 0x0000 
    ignore_ctl_error - Ignore any USB-controller regarding mixer
    		       interface (default: no)

    This module supports multiple devices, autoprobe and hotplugging.

    NB: nrpacks parameter can be modified dynamically via sysfs.
        Don't put the value over 20.  Changing via sysfs has no sanity
	check.
    NB: async_unlink=0 would cause Oops.  It remains just for
        debugging purpose (if any).
    NB: ignore_ctl_error=1 may help when you get an error at accessing
        the mixer element such as URB error -22.  This happens on some
        buggy USB device or the controller.


Make sure to read this page:
[http://alsa.opensrc.org/index.php/Edirol_UA-25EX]("http://alsa.opensrc.org/index.php/Edirol_UA-25EX")

---

### Post by lidex on 2010-07-06
I don't know, maybe specifying larger nrpacks. 

> Module snd-usb-audio
  --------------------

    Module for USB audio and USB MIDI devices.

    vid             - Vendor ID for the device (optional)
    pid             - Product ID for the device (optional)
    nrpacks	    - Max. number of packets per URB (default:8)
    async_unlink    - Use async unlink mode (default: yes)
    device_setup    - Device specific magic number (optional)
                    - Influence depends on the device
                    - Default: 0x0000 
    ignore_ctl_error - Ignore any USB-controller regarding mixer
    		       interface (default: no)

    This module supports multiple devices, autoprobe and hotplugging.

    NB: nrpacks parameter can be modified dynamically via sysfs.
        Don't put the value over 20.  Changing via sysfs has no sanity
	check.
    NB: async_unlink=0 would cause Oops.  It remains just for
        debugging purpose (if any).
    NB: ignore_ctl_error=1 may help when you get an error at accessing
        the mixer element such as URB error -22.  This happens on some
        buggy USB device or the controller.


Make sure to read this page:
[http://alsa.opensrc.org/index.php/Edirol_UA-25EX]("http://alsa.opensrc.org/index.php/Edirol_UA-25EX")

---

### Post by blablack on 2011-04-24
Hello Raboofje,

I'm running into the exact same issue (same sound card, another HP laptop but still these EHCI USB ports...).

Did you ever found a solution to this problem?

Thanks in advance,

---

### Post by dsx on 2011-06-30
I was working now for 2 day's on the problem:
"cannot submit datapipe for urb 0, error -28: not enough bandwidth".

finally - u cant imagine how simple it was - i found the reason and got my usb-sound back again.

the main reason was the "auto-mute feature" after changing audio source with pulse.

so try to go ahead.
 - open gnome-alsamixer or alsamixer
 - switch to tab USB Mixer
 - and increase master volume (Speaker) from zero to more...

here is the original source for this hint:
[http://forum.ubuntuusers.de/topic/medusa-5-1-usb-headset/#post-2532118](http://forum.ubuntuusers.de/topic/medusa-5-1-usb-headset/#post-2532118)

looks like the errormessage above has nothing todo with missing sound.

hope this will help.

regards
ds

---

