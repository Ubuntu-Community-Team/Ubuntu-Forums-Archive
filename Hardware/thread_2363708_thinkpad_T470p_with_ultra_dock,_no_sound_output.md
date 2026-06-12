---
title: "thinkpad T470p with ultra dock, no sound output"
date: 2017-06-13
forum: Hardware
---

### Post by joyliang on 2017-06-13
system: 17.04(4.10.0-22-generic)

I've view some other threads, and tried the following solutions:

add something to /etc/modprobe.d (tried lenovo-dock/thinkpad/tpt470p/... but not work)

add /lib/firmware/t470p.fw contains following (FROM [HERE]("https://bbs.archlinux.org/viewtopic.php?id=206304"))
[codec]
0x10ec0292 0x17aa2226 0
[pincfg]
0x16 0x21211010
0x19 0x21a11010

replaced 0x17aa2266 with 0x17aa505d (found by ```
alsa-info --stdout | grep 0x17aa
```)

but output option turned into "Dummy output" and even internal speaker stop working.

anybody solved this problem on T470p?

---

### Post by talekksna2 on 2017-06-29
I have same problem. I had Lenovo ThinkPad L450 with Ubuntu Gnome 16.04 TLS, and it is worked. But now, with ThinkPad T470p and Ubuntu Gnome 17.04, I don't have sound.

---

### Post by talekksna2 on 2017-10-23
Sill no sound on 17.10

---

### Post by viser-m on 2017-11-08
Have same problem on 16.04, 17.10 with T470, found this investigation [https://forums.gentoo.org/viewtopic-t-1061866-start-0.html](https://forums.gentoo.org/viewtopic-t-1061866-start-0.html)

---

### Post by snuupy2 on 2017-12-30
Same issue here. Haven't been able to get it to work. On Linux Mint 18.3.

---

### Post by adoption on 2018-07-06
also have a thinkpad T470p with ultra dock installed 18.04.
same problem
soundsetting: no input, only dummy output

alsa-info --stdout | grep 0x17aa ->

> cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
lspci: Unable to load libkmod resources: error -12
cat: /proc/asound/modules: No such file or directory
ls: cannot access '/dev/snd/*': No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1595: No soundcards found...
cat: /tmp/alsa-info.SBpcuPeeuk/alsactl.tmp: No such file or directory


---

