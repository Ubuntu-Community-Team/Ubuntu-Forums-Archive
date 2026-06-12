---
title: "Thinkvantage and Media Keys on Lenovo 3000 V100"
date: 2011-10-23
forum: Hardware
---

### Post by rmccarri on 2011-10-23
Hi Everyone,
This is a minor issue, but one of those things that's been bugging me.  Everything on my laptop works right after the install, including the camera and fingerprint reader (with fprint-demo) with the exception of the Thinkvantage and media player special keys. On my computer, these keys and dedicated mute and volume buttons are separate and above the actual keyboard.  I was wondering if I could get some tips for getting these two keys to work.  The volume and mute keys work fine.

I've used xev and hal and the Thinkvantage and media player keys do not register.  It would appear that they are on a separate connection or something.  Like I said, it's not that big of an issue, but they are literally the only hardware that's not working perfectly on my laptop.
Thanks in advance for any advice.
Rob

---

### Post by rmccarri on 2011-10-25
Just to give some extra information that might help, I popped off the panel and the Thinkvantage, Media Player, Mute, Volume Down and Volume Up keys are all on the same board.  They are connected to the motherboard with one of those band cables (what are those exactly?).  Here is how they are labeled on the circuit board:

Working Keys:
Mute - SW7
Volume Down - SW9
Volume Up - SW8

Non-Working Keys:
Thinkvantage - SW11
Media Player - SW6

---

### Post by rmccarri on 2011-10-25
And perhaps this might help.  I went though the hotkeys troubleshooting (still no key presses detected).  Here are the suggested outputs from that page.

---

### Post by rmccarri on 2011-10-25
It seems like this is probably a lost cause.  I've gone through all of the steps here:

[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

Including using the tools in /lib/udev and it just seems like the keys do not register at all.

Interestingly, there's a lenovo-3000 file in my /lib/udev/keymaps directory

```
0x8B switchvideomode # Fn+F7 video
0x96 wlan # Fn+F5 wireless
0x97 sleep # Fn+F4 suspend
0x98 suspend # Fn+F12 hibernate
0xB4 prog1 # Lenovo Care
```

I don't seem to have a 0xB4 key.

---

