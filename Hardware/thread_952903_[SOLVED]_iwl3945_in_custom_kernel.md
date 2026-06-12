---
title: "[SOLVED] iwl3945 in custom kernel"
date: 2008-10-19
forum: Hardware
---

### Post by Hazer on 2008-10-19
Hello,

I've recently compiled my own kernel but when I boot from it I cannot access my wlan (it doesn't detect the card) or use my sound card.  In the generic kernel for wifi the iwl3945 driver was automatically loaded and it worked fine but i cannot put it in my custom kernel as I think its a restricted module (no option do so on menuconfig) can anyone help? I really need a custom kernel.  My laptop is a sony vaio FZ21E

---

### Post by sdjcwcba on 2008-10-19
I had exactly the same issue when patching a kernel for HDAPS support.

Am also very interested in a solution :)

---

### Post by aldenhg on 2008-10-19
What does lspci give you? You might just need to run modprobe iwl3945 to get it running. If not, try depmod -a and then modprobe.

EDIT:
Durr, sorry. You probably need to rebuild the driver. Check out [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi) for instructions.

---

### Post by Hazer on 2008-10-28
Yay I did it! for the audio I just build in support for Intel HDA audio, and for the wifi I put the firmware ucode in /lib/firmware and integrated support for 3945BG card and it worked! typing on kernel 2.6.27.4!

Hope this helps!



:guitar:

---

