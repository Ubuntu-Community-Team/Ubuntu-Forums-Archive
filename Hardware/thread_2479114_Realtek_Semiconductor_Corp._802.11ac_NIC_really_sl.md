---
title: "Realtek Semiconductor Corp. 802.11ac NIC really slow connection"
date: 2022-09-14
forum: Hardware
---

### Post by draxavi on 2022-09-14
Hi

I am having my internet connection with the wifi dongle Realtek Semiconductor Corp. 802.11ac NIC really slow. It's is around 15~20, sometimes less than 5 in my computer with the dongle but in the notebook it's more than 100. I tried to find solutions around the web but none worked
dkms status returns:
rtl8192eu/1.0, 5.15.0-47-lowlatency, x86_64: installed
rtl8821CU/5.4.1, 5.13.0-40-generic, x86_64: installed
rtl8821CU/5.4.1, 5.13.0-41-generic, x86_64: installed
rtl8821CU/5.4.1, 5.13.0-41-lowlatency, x86_64: installed
rtl8821CU/5.4.1, 5.15.0-30-generic, x86_64: installed
rtl8821CU/5.4.1, 5.15.0-33-generic, x86_64: installedgrep: /lib/modules/5.13.0-41-lowlatency/build/.config: No such file or directory

rtl8821CU/5.4.1, 5.15.0-35-generic, x86_64: installedgrep: /lib/modules/5.15.0-33-generic/build/.config: No such file or directory
grep: /lib/modules/5.15.0-35-generic/build/.config: No such file or directory
grep: /lib/modules/5.15.0-37-generic/build/.config: No such file or directory
grep: /lib/modules/5.15.0-40-generic/build/.config: No such file or directory
grep: /lib/modules/5.15.0-41-generic/build/.config: No such file or directory

rtl8821CU/5.4.1, 5.15.0-37-generic, x86_64: installedgrep: /lib/modules/5.15.0-43-generic/build/.config: No such file or directory
grep: /lib/modules/5.15.0-46-generic/build/.config: No such file or directory
rtl8821CU/5.4.1, 5.15.0-40-generic, x86_64: installed
rtl8821CU/5.4.1, 5.15.0-41-generic, x86_64: installed
rtl8821CU/5.4.1, 5.15.0-43-generic, x86_64: installed
rtl8821CU/5.4.1, 5.15.0-46-generic, x86_64: installed
rtl8821CU/5.4.1, 5.15.0-46-lowlatency, x86_64: installed
rtl8821CU/5.4.1, 5.15.0-47-generic, x86_64: installed
rtl8821CU/5.4.1, 5.15.0-47-lowlatency, x86_64: installed
v4l2loopback/0.12.5, 5.13.0-41-lowlatency, x86_64: installedgrep: /lib/modules/5.13.0-41-lowlatency/build/.config: No such file or directory

v4l2loopback/0.12.5, 5.15.0-33-generic, x86_64: installedgrep: /lib/modules/5.15.0-33-generic/build/.config: No such file or directory

v4l2loopback/0.12.5, 5.15.0-35-generic, x86_64: installedgrep: /lib/modules/5.15.0-35-generic/build/.config: No such file or directory

v4l2loopback/0.12.5, 5.15.0-37-generic, x86_64: installedgrep: /lib/modules/5.15.0-37-generic/build/.config: No such file or directory

v4l2loopback/0.12.5, 5.15.0-40-generic, x86_64: installedgrep: /lib/modules/5.15.0-40-generic/build/.config: No such file or directory

v4l2loopback/0.12.5, 5.15.0-41-generic, x86_64: installedgrep: /lib/modules/5.15.0-41-generic/build/.config: No such file or directory

v4l2loopback/0.12.5, 5.15.0-43-generic, x86_64: installedgrep: /lib/modules/5.15.0-43-generic/build/.config: No such file or directory

v4l2loopback/0.12.5, 5.15.0-46-generic, x86_64: installedgrep: /lib/modules/5.15.0-46-generic/build/.config: No such file or directory

v4l2loopback/0.12.5, 5.15.0-46-lowlatency, x86_64: installed
v4l2loopback/0.12.5, 5.15.0-47-generic, x86_64: installed
v4l2loopback/0.12.5, 5.15.0-47-lowlatency, x86_64: installed
dpkg -l | grep 8812 returns nothing
lsmod | grep rtl returns nothing
also have this line from inxi -Fxxxrz && rfkill list && iwconfig
wlxa0d768202865  IEEE 802.11AC  ESSID:"DAVI-5G"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:5.2 GHz  Access Point: 78:E9:CF:DF:73:FE
          Bit Rate:434 Mb/s   Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/100  Signal level=-68 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
I tried to install drivers from git that I found in forums rtl8821CU
I tried to blacklist one of the drivers
None worked
The drivers I tried was this:
[https://github.com/brektrou/rtl8821CU.git](https://github.com/brektrou/rtl8821CU.git)
[https://github.com/clnhub/rtl8192eu-linux](https://github.com/clnhub/rtl8192eu-linux)


I tried to add this ppa: add-apt-repository ppa:linuxmint-tr/wireless-ppa
But it's don't exist

This is the blacklist:
rtl8192cu
GitHub
GitHub - clnhub/rtl8192eu-linux: Realtek rtl8192eu official Linux d...
Realtek rtl8192eu official Linux driver v5.2.19.1. Contribute to clnhub/rtl8192eu-linux development by creating an account on GitHub.
GitHub - clnhub/rtl8192eu-linux: Realtek rtl8192eu official Linux d...
and that's it
&#65279;

---

### Post by draxavi on 2022-09-14
Ok, I solved it somehow. It's was related to the USB port. Maybe the one I was using was 3.0 and the dongle support only 2.0? Don't know really. Just know that changing the port solved the issue.

---

