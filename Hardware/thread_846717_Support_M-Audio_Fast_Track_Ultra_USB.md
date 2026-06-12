---
title: "Support M-Audio Fast Track Ultra USB"
date: 2008-07-01
forum: Hardware
---

### Post by Linuxcore on 2008-07-01
Hello, I recently updated the hardware of my home studio recording, and I decided to dedicate a PC to the use of ubuntu as DAW, so as to start working up. I'am use Ubuntu for several years.
Are now 5 years that I dedicate to Membership and Registration in a professional, so I was wondering if on Linux I have support for the** M-AUDIO FAST TRACK ULTRA USB**, so that it can interface with **JACK** and all other professional applications on Linux.
I watched the forum, but in reference to this model nothing, something has jumped out from some other site but in vain ... the only useful reference that is approaching at least [http://ubuntuforums.org/showthread.php?t=447744]("http://ubuntuforums.org/showthread.php?t=447744")
In fact I wanted to point out to you all, as this theard I hope to become useful reference, which Hardy on UBUNTU 8.04, giving the command:

```

sudo asoundconf list

Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel
Ultra

```

this means that Linux itself recognizing .. other sign of life is given here:
```

cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux DharmaXP 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA Intel at 0xd2300000 irq 23
M-Audio Fast Track Ultra at usb-0000:00:1d.7-3, high speed

Audio devices:
0: STAC92xx Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
1: Fast Track Ultra

Timers:
7: system timer

Mixers:
0: SigmaTel CXD9872RD/K
1: mixer10

```

or

```

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd2300000 irq 23
 1 [Ultra          ]: USB-Audio - Fast Track Ultra
                      M-Audio Fast Track Ultra at usb-0000:00:1d.7-3, high speed

```

	
this is the log JACK at the M-Audio fast Track Ultra IN / OUT:

```

16:20:22.231 Startup script...
16:20:22.234 artsshell -q terminate
16:20:22.659 Startup script terminated with exit status=256.
16:20:22.660 JACK is starting...
16:20:22.660 /usr/bin/jackd -dalsa -r44100 -p256 -n2 -D -Chw:1 -Phw:1 -S
16:20:22.663 JACK was started with PID=8325.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|256|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:1
**ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode**
cannot load driver module alsa
no message buffer overruns
16:20:22.691 JACK was stopped successfully.
16:20:22.691 Post-shutdown script...
16:20:22.692 killall jackd
jackd: no process killed
16:20:23.099 Post-shutdown script terminated with exit status=256.
16:20:24.722 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```

how can I solve? Thank you who can help me.

Congratulations to the whole community :)

PS: My configuration Laptop is Sony Vaio FE-28H.

---

### Post by Linuxcore on 2008-07-02
when there is no solution?:confused:

---

### Post by Linuxcore on 2008-07-04
...............

---

### Post by buttertoad on 2008-07-05
It looks like you have on board audio also. Try disabling the Intel HDA in your BIOS, I did that and my M-Audio Delta 44 works great now.
Hope this is what you needed.

---

### Post by nigu on 2008-08-04
Hello, everyone. I've just got one of these babies and, guess what, it does not work on Ubuntu 8.04.

I have googled around and downloaded the ALSA source code with not much luck.

I intend to get on and start tinkering with the drivers. Has anyone got any information about the chipset that's on the card? Is anyone already developing a driver?

---

### Post by vivichrist on 2008-08-06
try playing with the settings. you really need the realtime kernel and modifications to limits.conf etc. read the ubuntustudio prep docs or something like that. I doubt whether it uses alsa my firepod uses freebob (firewire).

---

### Post by Linuxcore on 2008-08-15
thanks for the support:) unfortunately still have not solved .. input and midi work .. but nothing in output .. but why ubuntu detects it but not working? when you decide to make it work?
would not be possible to make a port windows driver on Linux?

---

### Post by asmallerbrain on 2009-12-08
This is really frustrating.  I have exactly the same problem.  Linux recognizes the (class-compliant!) audio interface.  I tried to use padevchooser to switch cards.  Fail.  Pulseaudio doesn't appear to know the card exists.  Disabling my onboard audio interface in the bios is simply not an option.

---

### Post by salvoinzk on 2010-01-08
Hi you all guys

Since the Fast Track Ultra seems to work in input.

Did someone checked, if something changes by using Fast Track in "input device" only, and the integrated audio card as "output device" only, under Jack?


Kind regards
Salvatore

---

### Post by salvoinzk on 2010-01-11
Hello everyone.

I found a forum where it seems that someone has contacted directly those of the ALSA team for some help about the "Fast Track Ultra", and the ALSA guys replayed him by sending a patch for the audio drivers that I copy below:




--- linux/sound/usb/usbaudio.c
+++ linux/sound/usb/usbaudio.c
@@ -2235,6 +2235,10 @@ static void init_substream(struct snd_us
                case USB_ID(0x041e, 0x3f0a): /* E-Mu Tracker Pre */
                        subs->ops.retire_sync = retire_playback_sync_urb_hs_emu;
                        break;
+               case USB_ID(0x0763, 0x2080): /* M-Audio Fast Track Ultra */
+                       subs->ops.prepare_sync = prepare_playback_sync_urb;
+                       subs->ops.retire_sync = retire_playback_sync_urb;
+                       break;
                }
        }
        snd_pcm_set_ops(as->pcm, stream,
@@ -2786,6 +2790,7 @@ static int parse_audio_endpoints(struct
                        break;
                case USB_ID(0x041e, 0x3020): /* Creative SB Audigy 2 NX */
                case USB_ID(0x0763, 0x2003): /* M-Audio Audiophile USB */
+               case USB_ID(0x0763, 0x2080): /* M-Audio Fast Track Ultra */
                        /* doesn't set the sample rate attribute, but supports it */
                        fp->attributes |= EP_CS_ATTR_SAMPLE_RATE;
                        break;
--- linux/sound/usb/usbquirks.h
+++ linux/sound/usb/usbquirks.h
@@ -1864,6 +1864,33 @@
                }
        }
},
+{
+       USB_DEVICE_VENDOR_SPEC(0x0763, 0x2080),
+       .driver_info = (unsigned long) & (const struct snd_usb_audio_quirk) {
+               /* .vendor_name = "M-Audio", */
+               /* .product_name = "Fast Track Ultra", */
+               .ifnum = QUIRK_ANY_INTERFACE,
+               .type = QUIRK_COMPOSITE,
+               .data = & (const struct snd_usb_audio_quirk[]) {
+                       {
+                               .ifnum = 0,
+                               .type = QUIRK_IGNORE_INTERFACE
+                       },
+                       {
+                               .ifnum = 1,
+                               .type = QUIRK_AUDIO_STANDARD_INTERFACE
+                       },
+                       {
+                               .ifnum = 2,
+                               .type = QUIRK_AUDIO_STANDARD_INTERFACE
+                       },
+                       /* interface 3 (MIDI) is standard compliant */
+                       {
+                               .ifnum = -1
+                       }
+               }
+       }
+},

/* Casio devices */
{


It also seems that a user has applied this patch for his "Fast Track Ultra 8R", and it works.

The fact is that I am not able to recompile the kernel, I actually had 2 not good experiences, about it, so do it as you like.
For sure if the ALSA guys had given to him directly the sound-driver already patched, it would be much better!


There also I copy the link of the forum (two pages) where I found what was written up there:

[http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&st=0&sk=t&sd=a&start=15](http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&st=0&sk=t&sd=a&start=15)


Greetings to all
Salvo

---

### Post by salvoinzk on 2010-01-13
Maybe you don't need to recompile the whole kernel, but only the ALSA driver.
I mean you have to apply the previous patch to ALSA driver and then compile it. 


Try to read my posts on the forum, at the following link:

[http://www.linuxmusicians.com/viewto...1&p=9822#p9822]("http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&p=9822#p9822")

---

### Post by salvoinzk on 2010-01-20
Hi you all

it seems that a french guy was able to make work the Fast Track Ultra (= FTU)

I don't understand the french language but, it seems, he applied the previous patch to the kernel and then recompiled it again, and now the FTU works.

here is the link:
[http://www.linuxmao.org/tikiwiki/tiki-view_forum_thread.php?topics_offset=1&forumId=2&comments_parentId=16414](http://www.linuxmao.org/tikiwiki/tiki-view_forum_thread.php?topics_offset=1&forumId=2&comments_parentId=16414)

hope this help !


ps: here the english translation of the above site:
[http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.linuxmao.org%2Ftikiwiki%2Ftiki-view_forum_thread.php%3Ftopics_offset%3D1%26forumId%3D2%26comments_parentId%3D16414&sl=auto&tl=en](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.linuxmao.org%2Ftikiwiki%2Ftiki-view_forum_thread.php%3Ftopics_offset%3D1%26forumId%3D2%26comments_parentId%3D16414&sl=auto&tl=en)


bye

---

### Post by crashputer on 2010-09-16
I own a Fast Track Ultra 8r, and was able to use it for recording and playback within Audacity.

I used Ubuntu 10.10 beta, and simply plugged the device in, and within audacity set the interface to ALSA and the record and playback device to the M-audio option. By default the 8r handles audio at 48KHz, so don't forget to change your project sample rate.

Edit: I tested with Ardour/Jack and it worked perfectly.

I was not able to set the 8r as the global recording or playback device.

---

### Post by kinta on 2010-11-18
Iwas thinking about buying this soundcard. After searching if compatible. It seems that the patch is already in the kernel 2.6.35(maverick one). look at :[ http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.35.y.git;a=commitdiff;h=fca5bca48759c21eddc0667a4582a227d7b0165a;hp=85ae01b2da0ed606a2e8d840aadef90fd30220a1]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.35.y.git;a=commitdiff;h=fca5bca48759c21eddc0667a4582a227d7b0165a;hp=85ae01b2da0ed606a2e8d840aadef90fd30220a1")
:popcorn:

---

### Post by kinta on 2010-12-15
Can somebody change this thread as [RESOLVED] ???

---

