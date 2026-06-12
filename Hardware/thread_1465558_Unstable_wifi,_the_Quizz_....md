---
title: "Unstable wifi, the Quizz ..."
date: 2010-04-29
forum: Hardware
---

### Post by morticul on 2010-04-29
Hi all.

I'm experiencing some "hard to track" instability with my wifi. The wifi works, I can go to the internet but it often cuts for several seconds. It doesn't really disconnect. It just stop working and then comes back.

The problem can come from 4 different places.

[LIST]
[*]router (D-link DIR-655 v1.02)
[*]wifi card (BCM4312)
[*]wifi driver (how can I tell)
[*]The rest of the system (dell 11z, ubuntu 9.10, 2.6.31-20, i686)
[/LIST]

So... here is the quizz :
Place your bet on which part of the system the problem comes from and, optionally, suggest a way to verify your affirmation. 

I've attached some hints to help you ...

With ifstat, I've collected data and (using the attached python script), I've plotted the data to ifstat.pdf (attached file).

The graph clearly shows the on/off pattern. Sometime, it stop cutting and then it comes back. Using a wired connection, this beautiful pattern goes away. Unfortunately, my girlfriend don't want me to keep this blue filiform decoration. So I must solve this wifi problem.

---

### Post by cookdav on 2010-05-01
Best not to have 'quizzes' when you don't understand how
to know what driver you are using.

But since you like quizzes :razz:, decipher this:

alias show-config-installcmd='cd /usr/local/bin && wget -Nc smxi.org/inxi && chmod +x inxi'

alias show-config='inxi -xrFA'

Note that these aliases come from a 'non-sudo' Debian world, so do
a 'sudo konsole' before you do the first one (a one-shot series of root cmds).

The second should be done as a normal user.

You could even post back the output of the second one.

And, most importantly, tell us what kind of wifi-security
you have in place, as I'm guessing that it might be an 'encryption' issue, 
and if so, if you setup your router to 'open'
security, the problem would go away.

I'm betting that you have the 'b43' driver. ;)

---

### Post by morticul on 2010-05-03
Quizzes are always fun :p

Further investigations tells me it is a router problem (I've been having the same on/off pattern on another computer). I'll be trying without the WPA security as you said. It is a good Idea. Next step will be to flash the firmware of the router.

Any idea on how to isolate a little bit more the problem before flashing the firmware ?

For now, here is the output of inxi.
Thanks.

```

$ ./inxi -xrFA
System:    Host procrastinatron Kernel 2.6.31-20-generic i686 (32 bit) Distro Ubuntu 9.10 karmic
CPU:       Single core Intel Celeron 743 (UP) cache 1024 KB flags (lm nx sse sse2 sse3 ssse3) bmips 2592.95 clocked at 1296.479 MHz 
Graphics:  Card Intel Mobile 4 Series Chipset Integrated Graphics Controller tty res: 157x40 
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller driver HDA Intel BusID: 00:1b.0
           Sound: Advanced Linux Sound Architecture Version 1.0.20
Network:   Card-1 Broadcom BCM4312 802.11b/g driver wl BusID: 08:00.0
           Card-2 Attansic Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter driver atl1c v: 1.0.0.1-NAPI at port 2000 BusID: 02:00.0
Disks:     HDD Total Size: 560.1GB (43.7% used) 1: /dev/sda WDC_WD1600BEVT 160.0GB 
           2: USB /dev/sdc 4000BEV_External 400.1GB 
Partition: ID:/ size: 19G used: 4.5G (26%) fs: ext4 ID:swap-1 size: 1.00GB used: 0.00GB (0%) fs: swap 
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://ca.archive.ubuntu.com/ubuntu/ karmic main restricted
           deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic main restricted
           deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
           deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
           deb http://ca.archive.ubuntu.com/ubuntu/ karmic universe
           deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic universe
           deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates universe
           deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-updates universe
           deb http://ca.archive.ubuntu.com/ubuntu/ karmic multiverse
           deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic multiverse
           deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
           deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
           deb http://security.ubuntu.com/ubuntu karmic-security main restricted
           deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
           deb http://security.ubuntu.com/ubuntu karmic-security universe
           deb-src http://security.ubuntu.com/ubuntu karmic-security universe
           deb http://security.ubuntu.com/ubuntu karmic-security multiverse
           deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
           deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
           deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
Info:      Processes 155 Uptime 1 day Memory 486.2/1943.7MB Runlevel 2 Client Shell inxi 1.4.9 


```

---

### Post by morticul on 2010-05-09
For now, changing to WEP encryption seems to provide a stable connection. However, since I would like to use a WPA encryption, I'll try further tests.

* Using b43 driver
* Using only WPA1
* Using only WPA2

Meanwhile here are the scripts I uses to verify if I solved the problem or not. Since the only symptoms I have is some random instability over few hours. I did a script (getData.py) that download a file using wget at 20kB/s while periodically read the size of the file and the sent/received bytes from /proc/net/dev. Finally, using plotData.py, this provide a graphic of the stability. Hope this could be useful to anyone ...

---

### Post by sir83 on 2010-06-05
Hi,

Have you found a solution to your WPA problem?

I think I have the same issue as you, the transfer speed slows down periodically. See attached picture:
[http://i.imgur.com/BeZt6.png](http://i.imgur.com/BeZt6.png)

OS: Ubuntu 10.04
Wificard: BCM4312
Laptop: HP Compaq 6715b

---

