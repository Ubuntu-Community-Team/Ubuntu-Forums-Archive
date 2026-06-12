---
title: "Bluetooth does not work Ubuntu 16.04"
date: 2018-02-01
forum: Hardware
---

### Post by greenfrog42 on 2018-02-01
No matter what type of Bluetooth headset I try, it will not work.  It connects but every time I try to test speakers it disconnects.

Any ideas or does 16.04 just sucks with Bluetooth devices.

Thanks

---

### Post by jacopastorius82 on 2018-02-01
Hi, i had problems too. Solved with this:
```
sudo apt-get install pulseaudio-module-bluetooth
pactl load-module module-bluetooth-discover
```
Then, if your audio quality is low, you have to set the profile as ad2p
```
wget https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae/archive/d698974910bbb7d016ec0ad08c1bf41b4b524364.zip
```
download this and launch the script

---

### Post by greenfrog42 on 2018-02-01
[COLOR=#000000][FONT=&amp]pactl load-module module-bluetooth-discover
[/FONT][/COLOR]Failure: Module initialization failed

Headset now pairs, but when I go to Sound to test it, does not show up, just the internal speakers.

Works great under Windows 10.

---

