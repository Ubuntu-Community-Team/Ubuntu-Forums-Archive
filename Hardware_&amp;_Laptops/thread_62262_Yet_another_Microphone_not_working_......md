---
title: "Yet another Microphone not working ....."
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by niobe_logos on 2005-09-04
I installed Hoary onto a Toshiba Satellite A65. After following most of the suggestions in the Unofficial Guide--especially the sound configuration ones--most stuff works great. Movies play without dropping frames, streamtuner does beautiful Internet Radio, music CD's play and rip without a hitch. I just installed Skype, and everything there works terrific too--it makes calls with no problems. But I can't hold up my end of the conversation, because the microphone is not working!

 ](*,) 

At this point, I like other Ubuntu forum folks have:
Followed the sound configuration suggestions in the Guide
Set and reset many settings in Alsamixer (the only results I have now is extremely loud feedback, but no recording capability)
Set and reset things in the Multimedia Selector, Right now I have things set to ALSA for output and OSS for input. If I set ALSA for input, I get the "ALSA device "default" had an error" message when recording.

So any suggestions, ideas, etc on how to fix this would be welcome. Thanks in advance!

Okay, some logs for you:


lspci:
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device cab3 (rev 05)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4437
0000:02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

asound.conf:
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

/proc/asound/cards: 
0 [IXP            ]: ATIIXP - ATI IXP
                     ATI IXP rev 0 with ALC250 at 0xf0000400, irq 17
1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                     ATI IXP Modem rev 1 at 0xf0000500, irq 17

/proc/asound/devices:                                                     # &#9474;&#9474;   0: [0- 0]: ctl
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
 33:       : timer
 32: [1- 0]: ctl
 48: [1- 0]: digital audio playback
 56: [1- 0]: digital audio capture

---

### Post by niobe_logos on 2005-09-04
SOLVED!  Kinda.

Like everyone else I kept messing with alsamixer, and then tried Skype's "echo123" test to see if anything was getting through. And it is....sorta. Turns out the microphone jack is messed up, so that if it's plugged all the way in, it cuts out sound altogether, while pushing it in partway will allow sound to be captured, but not consistently. 

So now all I have to do is figure out how to make a USB headset work,  :roll: and that should solve the jack problem.

---

