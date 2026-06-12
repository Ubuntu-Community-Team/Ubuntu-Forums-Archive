---
title: "HP DV6 1115 EV laptop, Hybrid Graphics. Proprietary Driver no screen found error."
date: 2012-02-27
forum: Hardware
---

### Post by Andy_9000 on 2012-02-27
Hello all,

I don't run an ubuntu variant at the time however I decided to post this here since the Ubuntu forums are quite active and would be a good place to get some help maybe.

I run a debian variant, Crunchbang 64 bit BPO with the 3.2.0 kernel.


Immediately after installing the AMD drivers succesfully on it and working for about an hour, I had to log out of the session in order to restart some scripts. Upon logging out i was met with an Xorg error screen which said the following in the error parts. 

(EE) Screen 1 deleted because of no matching config selection
(EE) fglrx(0): PowerXpress: usr/lib64/fglrx/switchlibGL failed with exit status 1
(EE) fglrx(0): PowerXpress: Failed to switch libGL link files.
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error: No screens found.

Before logging out everything worked normally, but after that, even after many reboots it's stuck with that message and I'll be stuck in TTY.

Anyone has any ideas as to why this happened or how I could fix it? I searched a lot but didn't find the same error anywhere.


Thank you.

ps.
the GPU is an HD6770, the integrated GPU is an intel.
the chipset is an HM65 and the cpu is an Intel i7

---

### Post by Yellow Pasque on 2012-02-27
This should get you back to your original graphics config: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch)
You may also need this command:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

As for actually getting the ATI proprietary driver working, it's complicated right now: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

