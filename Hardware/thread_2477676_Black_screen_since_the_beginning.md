---
title: "Black screen since the beginning"
date: 2022-08-03
forum: Hardware
---

### Post by miguel30 on 2022-08-03
[COLOR=#232629][FONT=-apple-system]Hi,

This is the first time that I've installed Ubuntu, and it's a dual boot. Ubuntu is installed on a 500GB SSD. It loads to a black screen and doesn't allow any hotkeys to invoke a terminal. If I boot into failsafe mode it loads a default GUI fine (it doesn't adapt to my screen size, but at least it loads), but obviously that's not ideal.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]My graphics card is a AMD Radeon RX 550. AFAIK I downloaded the proprietary drivers just fine, but nothing seems to work. I have no idea what to do now, and I will be forced to uninstall the whole thing if it doesn't work.

[/FONT][/COLOR]
dpkg -l amdgpu-install
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version               Architecture Description
+++-==============-=====================-============-=========================>
ii  amdgpu-install 22.10.2.50102-1416363 all          AMDGPU driver repository

---

### Post by drumone on 2022-09-07
Did you recently download the AMD GPU software/drivers for your machine? I tried doing that today and I'm having the same issue. I haven't tried a safe boot yet, but will be doing that next.

---

