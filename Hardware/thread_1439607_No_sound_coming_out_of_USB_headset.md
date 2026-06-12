---
title: "No sound coming out of USB headset"
date: 2010-03-26
forum: Hardware
---

### Post by elektrisk564 on 2010-03-26
Hello.
I have Ubuntu 9.10, and am trying to get my headset to work with it. It's a USB headset, not a bluetooth headset. Anyway, the input is working. I switched my input from my internal mic to my USB one in my sound settings, and that fixed that. However, even if I set my output device to the USB, it still doesn't work. Does anyone have any advice? It works on Windows.

The headset is: Planet UP-100, Genius G-Talk
Here's lsusb:
```
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0d8c:000e C-Media Electronics, Inc. Audio Adapter (Planet UP-100, Genius G-Talk)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by elektrisk564 on 2010-03-26
Bump. Please help if you have time.

---

### Post by macogw on 2010-03-26
Install pavucontrol, run it, and select the stream that you want to go through USB, then tell it to do that.

---

### Post by Austin25 on 2010-03-26
I don't want to sound condescending because I have done this before: what is your volume setting?

---

### Post by elektrisk564 on 2010-03-26
> **macogw said:**
> Install pavucontrol, run it, and select the stream that you want to go through USB, then tell it to do that.

> **Austin25 said:**
> I don't want to sound condescending because I have done this before: what is your volume setting?

I set the 'output' option to my headset and it still didn't work.

---

### Post by pricinosus on 2012-01-08
Maybe is to late for you elektrisk564 but not for others ;)

In terminal type
alsamixer
[IMG]http://img27.imageshack.us/img27/7602/96912024.png[/IMG]

then hit F6
[IMG]http://img214.imageshack.us/img214/6498/18292302.png[/IMG]

choose Generic USB Audio device
[IMG]http://img214.imageshack.us/img214/9250/17493931.png[/IMG]

keep pressed: up arrow key
[IMG]http://img197.imageshack.us/img197/995/97295160.png[/IMG]

[IMG]http://img100.imageshack.us/img100/9572/42663781.png[/IMG]

---

### Post by caiorearte on 2012-02-01
Hey, thanks! Finally got this thing working. My in-ear headphones get noticeably hotter when using the USB card, though, I'm afraid it might damage them. Plus, it's quite uncomfortable...

---

### Post by VpNKBQLjz0 on 2012-04-13
I just wanted to say: 'pricinosus' you are a legend.

Thank you so much man. Fixed my problem immediately. I wish I could buy you a coffee or something. I've been trying for ages to get this card to work..

I'm so glad it's linux compatible.

Aaah time to enjoy some music!
Now if I could only get flash player working...

EDIT: It seems I have to do this every time at boot, is there any way to make the settings stick so I don\t have to run this command and do this every time at boot?

Nvm worked it out myself.

Turn your USB sound card up to 90%. Not 100% because ubuntu/whatever distro you use, pushes more power through the card than Windows does. You can heat up your earphones and potentially break your cheap USB soundcard & microphone. So set the levels to about 90% or so, just to be safe, lower is better and it's still loud as.

Then when you are done.

> Hit Esc.
Keep the terminal open
Type 'sudo alsactl store'
Press Ctrl + D
Type 'sudo reboot'

Done!

---

