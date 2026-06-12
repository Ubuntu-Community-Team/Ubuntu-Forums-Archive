---
title: "No Sound on new HP2000-140CA Laptop"
date: 2011-06-22
forum: Hardware
---

### Post by handyman on 2011-06-22
I'm having problems getting things working on my new laptop under Ubuntu 10.04. I found and installed the wireless driver successfully but am having no luck with the sound card driver.

The command "aplay -l" returns;
aplay: device_list:223: no soundcards found...

"lspci -v" returns a long list including;
00:14.2 Audio device: ATI Technologies Inc. SBx00Azalia (Intel HDA) (rev 40)
        Subsystem: Hewlett-Packard Company Device 3577
        Flags: bus master, slow devsel, latency 32, IRQ4
       
Can anyone tell me how to solve this problem? I have so far been unsuccessful in my search for a driver. :(

---

### Post by gordintoronto on 2011-06-22
Follow the instructions on this page: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
Or install Ubuntu 11.04.

---

### Post by handyman on 2011-06-27
Thanks so much gordintoronto, that solved my problem.:p

---

