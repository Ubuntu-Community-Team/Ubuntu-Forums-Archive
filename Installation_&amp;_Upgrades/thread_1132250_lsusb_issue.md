---
title: "lsusb issue"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by rymar115 on 2009-04-21
Upgraded to 9.04 rc. Love it. Except I am having an issue with lsusb. when executed from terminal I get no response it just goes back to the prompt. Now all of my usb devices work fine, Logitech Mouse, webcam, keyboard, printers etc. However this all started with trying to install the scanner component of my Brother mfc240c printer. I have been unable to get the scanner to work (worked in 8.10) and I suspect in the process I have corrupted or messed up something. I am relative new to Ubuntu and Linux in general, but I have tried it on and off since the beginning. Thanks for any help anyone can offer me it's got me stumped.

---

### Post by rymar115 on 2009-04-22
well still battling this issue. However since I have tried a couple of things. 

/home/ryk# lsmod | grep usb
snd_usb_audio          90400  0 
snd_usb_lib            24320  1 snd_usb_audio
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss,snd_usb_audio
snd_rawmidi            29696  2 snd_usb_lib,snd_seq_midi
snd_hwdep              15108  1 snd_usb_audio
snd                    62628  17 snd_hda_intel,snd_pcm_oss,snd_usb_audio,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep
usblp                  20224  0 
usbhid                 42336  0 
usb_storage            82880  2 

root@ryk-desktop:/home/ryk# lsusb
root@ryk-desktop:/home/ryk#

root@ryk-desktop:/home/ryk# modprobe usbcore
FATAL: Module usbcore not found.

I have devoted some time to this if anyone could help me please

---

### Post by rymar115 on 2009-05-01
Finally solved this problem. Upgrading form 8.10 to 9.04 RC1 to 9.04 final had created some major issues. Corrupted config files etc. Did a clean install and everything is well again. Found a really easy way to restore all of Thunderbird's settings, email, addresses. Email me for details if you get stuck on this.

---

