---
title: "Tx1000 Audio problem. no device audio device in /dev/snd. Help!"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by tablet on 2008-01-29
Hallo,

This is my first time I install linux on my hp tx1250eg. The audio doesnt work. I've tried everything. 

I installed alsa and everything. Followed all tx1000 posts, but I coudnt find an answer.

Turns out that in the kernel, the sound device is not installed (not compiled?)

Here is on my /dev/snd

drwxr-xr-x  2 root root       80 2008-01-29 10:14 .
drwxr-xr-x 12 root root    14100 2008-01-29 10:49 ..
crw-rw----  1 root audio 116,  1 2008-01-29 10:14 seq
crw-rw----  1 root audio 116, 33 2008-01-29 10:14 timer

There is no /dev/dsp.

I checked with : dpkg -l linux-ubuntu-modules-*

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name             Version          Description
+++-================-================-================================================
ii  linux-ubuntu-mod 2.6.22-14.37     Ubuntu supplied Linux modules for version 2.6.22
ii  linux-ubuntu-mod 2.6.22-14.37     Ubuntu supplied Linux modules for version 2.6.22

I tried to reinstall the kernel:  sudo apt-get install linux-ubuntu-modules-2.6.22-14-generic

but it said that I already have the newest one.

so, please somebody help me..... 

thx in advance.

=====
tablet

---

