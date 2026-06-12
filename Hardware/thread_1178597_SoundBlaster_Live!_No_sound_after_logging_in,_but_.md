---
title: "SoundBlaster Live! No sound after logging in, but the initial drum heard"
date: 2009-06-04
forum: Hardware
---

### Post by lagu2653 on 2009-06-04
I have a Sound Card, SoundBlaster Live! (EMU10K), On the Line Out I have sound all the time, but on the Phones line I only have sound prior to logging in. I hear the initial drum sound, but after logging in the sound is gone. I have a SuSE/Ubuntu Dual boot so I have no /boot/loader.conf or /boot/grub.conf or /boot/grub/grub.conf. I use the SuSE boot menu. Is there a file which I need to edit? I've tried the mixers, changing all of the levels. Nothing helps.

---

### Post by santosh.puranik on 2009-09-03
Hi,

    I had this exact problem on my PC. Fixed by adding my username to the group "audio".

Ex.: sudo gpasswd -a username audio

Logout, and login again, you should have sound now. Hope this helps!

Santosh

---

