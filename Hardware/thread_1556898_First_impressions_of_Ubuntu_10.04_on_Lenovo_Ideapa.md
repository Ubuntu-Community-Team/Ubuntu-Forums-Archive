---
title: "First impressions of Ubuntu 10.04 on Lenovo Ideapad Z560"
date: 2010-08-20
forum: Hardware
---

### Post by absolutezero1287 on 2010-08-20
As the title of the thread states I have installed the 64-bit version of Ubuntu on my Lenovo Ideapad Z560. The Z560 came preinstalled with Windows 7 Home Premium. Upon installing Ubuntu I noticed that the laptop ran much faster. Unfortunately, I also noticed that the touchpad didn't work. I am using a USB mouse for now. The integrated camera worked great. I tested it using Cheese Webcam Booth. My only complaint was that the picture quality was a bit sharper under Windows 7 but other than that it works fine.

The media buttons that control the screen's brightness and the speaker's volume worked out of the box. I was very impressed at that. One interesting feature the laptop has is the one-touch recovery button. Under Windows 7 it saves your data to a disk image in a spare partition and uses it to recover should anything go wrong. I don't know if it works because I haven't tested it but I'm not that tempted to try. Wifi and Bluetooth work out of the box.

Specs:
Intel Core i5-540M Processor @ 2.53GHz 
4 GB RAM
Nvidia Geforce 310M 512MB
4 GB DDR3 SDRAM


Below are the last 60 lines of dmesg for those that are interested
```

[  137.470077] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  137.480384] psmouse.c: Touchpad at isa0060/serio1/input0 - driver resynched.
[  137.493883] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  137.503649] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  137.513530] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  137.524789] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  137.534489] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  137.534492] psmouse.c: issuing reconnect request
[  138.764778] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  138.774079] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  138.783944] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  138.793686] psmouse.c: Touchpad at isa0060/serio1/input0 - driver resynched.
[  138.802219] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  138.811351] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  138.823264] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  138.832946] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  138.842613] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  138.842616] psmouse.c: issuing reconnect request
[  190.373026] wlan0: deauthenticating from 00:16:b6:bc:36:b9 by local choice (reason=3)
[  190.373063] wlan0: direct probe to AP 00:16:b6:bc:36:b9 (try 1)
[  190.376762] wlan0: direct probe responded
[  190.376767] wlan0: authenticate with AP 00:16:b6:bc:36:b9 (try 1)
[  190.378707] wlan0: authenticated
[  190.378735] wlan0: associate with AP 00:16:b6:bc:36:b9 (try 1)
[  190.381199] wlan0: RX AssocResp from 00:16:b6:bc:36:b9 (capab=0x431 status=0 aid=2)
[  190.381203] wlan0: associated
[  190.393240] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  191.444905] alg: No test for __aes-aesni (__driver-aes-aesni)
[  191.444947] alg: No test for __ecb-aes-aesni (__driver-ecb-aes-aesni)
[  191.444993] alg: No test for __cbc-aes-aesni (__driver-cbc-aes-aesni)
[  191.448381] alg: No test for __ecb-aes-aesni (cryptd(__driver-ecb-aes-aesni))
[  191.457301] padlock: VIA PadLock not detected.
[  201.205345] wlan0: no IPv6 routers present
[  721.591383] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  721.600079] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  721.609516] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  861.300039] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  861.310083] psmouse.c: Touchpad at isa0060/serio1/input0 lost sync at byte 4
[  861.310087] psmouse.c: issuing reconnect request

```

If anyone has any idea at all why the touchpad isn't working I'd really appreciate the help. I messed with the options under System> Preferences> Mouse to see if it would help but it didn't.

---

### Post by absolutezero1287 on 2010-08-21
Update: USB mouse seems to stop working if I touch the touchpad. The touchpad still isn't working.

I'm not sure if its the fact that I'm on the 64bit version but I'm going to test the 32bit version and see if there's any improvement.

Also, is there any way to get 64bit flash working?

---

### Post by tnoh on 2010-09-25
I have the exact same issue with my Lenovo IdeaPad Z560.  Were you able to find a solution?

---

### Post by absolutezero1287 on 2010-09-25
See this [post.]("http://ubuntuforums.org/showpost.php?p=9175201&postcount=44") If you don't want to do that you can use a workaround. In /etc/modprobe.d/ directory make a file called touchpad.conf. Add the line "options psmouse proto=imps" and restart your computer.

If you would like to check out some more specific issues with the ideapad check out [my post]("http://ubuntuforums.org/showthread.php?t=1574679")

---

### Post by sandeep.gec on 2010-09-29
Hey thanks buddy..I was having trouble with the touchpad in my lenovo B460..

I went the touchpad.conf route, and it worked perfectly fine :)

---

### Post by absolutezero1287 on 2010-09-29
> **sandeep.gec said:**
> Hey thanks buddy..I was having trouble with the touchpad in my lenovo B460..

I went the touchpad.conf route, and it worked perfectly fine :)

Remember that its a workaround. The problem isn't really "solved" but rather avoided.

---

### Post by AG* on 2010-10-26
Thanks a lot! the workaround worked amazingly fine..

Are there any disadvantages of not using the other elaborated method..

I have a z560 machine, i3, 3gb, nvidia ..

I am a new user to ubuntu and thanks to you guys, I swear by it now!!

---

### Post by AG* on 2010-10-26
[st.]("http://ubuntuforums.org/showpost.php?p=9175201&postcount=44") If you don't want to do that you can use a workaround. In /etc/modprobe.d/ directory make a file called touchpad.conf. Add the line "options psmouse proto=imps" and restart your computer.
If anybody (like me) is wondering how to do it..then here is the way:

First switch to root user or do sudo (ubuntu keeps the root unlocked, to set a password you need to sudo passwd root and re-enter new UNIX password)

once you are root do this:cd /etc/modprobe.d/ && touch touchpad.conf
echo "options psmouse proto=imps" >> touchpad.conf

It works like gold after that..

---

