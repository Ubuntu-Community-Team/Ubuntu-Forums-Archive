---
title: "HP Envy with Beats Audio 2.1 Realtek"
date: 2015-09-16
forum: Hardware
---

### Post by inverged on 2015-09-16
I have an HP Envy [m6-n010dx]("http://support.hp.com/us-en/document/c04223655#AbT1").Running Elementary(Ubuntu 14.04)This is an AMD based model,which includes Beats Audio in the form of 2 speakers and an integrated subwoofer.
It uses Realtek ALC3241 sound card/chip.I can not get the subwoofer to work at all,and the sound is laughable compaired to Beats on Windows 8.
I have read many posts regarding this and have tried many of the suggestions,such as adding options snd-hda-intel model=ref to alsa-base.conf,enabled lfe remixing,
and changed the amount of sample channels.WHen using HDAJackRetask,I set one of the unconected pins to LFE Speaker,and Alsamixer shows a bass speaker that can be muted or unmuted,but there is no volume level for it,and no change to my sound.Depending on the pins I connect,different things show up in alsamixer,but they have no volume levels,only mute or output.I feel like I've tried everything,and any help would be appreiated.Let me know if you'd like to see my aplay or lspci | Audio outputs.
Thanks in advance.

---

