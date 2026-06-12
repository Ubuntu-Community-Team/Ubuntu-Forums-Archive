---
title: "Total Freezeof Ubuntu  (no kernel panic !!!)"
date: 2008-08-07
forum: General Help
---

### Post by SpaceTeddy on 2008-08-07
Hi Folks, 

this is the second time in two days that my computer totally froze. It never did not on Gutsy, and very, very occasially did so in Hardy before. But as far as i know i needed some heavy requirement for my laptop to freeze... 
There were
 - Compiz enabled
 - multiple, separated Firefox profiles running
 - one or more encrypted tunnels via Openvpn in usage
 - heavy data transfer through multiple proxies (heavy meaning 1Mbyte/sec or more)
 - music and/or videos running

By now, i have given up on compiz (way too much trouble at this point...)

In the past two days, i have not even come close to using any of this. Last night, i was watching a movie when the computer suddenly froze (watched via a sshfs mount). Today, it froze while i was listening to music and writing a response in this forum. That is hardly considered anything unusual anymore. 
Also, these are not kernel panics. If it where, the scroll and numlock would be blinking - which they are not doing. Yet, everything is dead. Even a remote login via ssh (which is running on my computer) is not possible anymore. So if this is the x-server crashing, it takes everything with it. 

Has anybody got any idea what could be causing this ? Or any idea how i can narrow the problem down ? I cannot have my computer crashing once a day - i do too many thing with it for that to happen. 

What i forgot to mention - last night and today i was using the computer from standy before... maybe that playing into it aswell ?

any help is appreciated :)

PS: if you need any specific specs of my computer, just ask. In general, i have a Samsung X60 with 2G RAM and a ATI X1600.

---

### Post by SpaceTeddy on 2008-08-12
ok... so nobody got any ideas...
i'll just keep posting more info, maybe something rings a bell at some point for someone. I am totally lost at the moment.

I've had two more crashes:
One when i was pairing with a bluetooth mobile phone. Put in the passkey, and the computer froze (to the joy of the dude with the mobile - he was a total Mac fan - he's been making fun of me ever since... :) )

Last one was just now - i've been happily downloading some files (about 700KByte/sec) and playing sudoku (this time i had no music running !) - freeze.

My theory that this has something to do with the audio/video is thus proven to be wrong. I am suspecting the network at the moment - but why this should happen i have no idea. Also, this happens with the wireless as well as the ethernet nic...

Also, i've run the memtest - two passes, no errors. I guess this is not a faulty ram. 

anybody.. please ?

---

### Post by hal8000 on 2008-08-12
Hi a few things to try:

Is it hardware or software:
Do you have a copy of Knoppix Live CD? If yes you can boot with this, ethernet uses DHCP so you should be able to use internet connection.

If all appears ok, then you are looking at a software or configuration issue with ubuntu, if however knoppix freezes then you are looking at a hardware problem.

If you suspect hardware:
Make sure its not temperature related, you could try removing the computer case and see if more air flow makes a differenece.
Make sure all fan inlets are clear of dust
Also make sure that the fans are working (which you should here or see if case removed).


If you suspect software:
Have a look in /var/log/messages for clues.
You can also try /var/log/Xorg.0.log for anything unusual as well.

I hate these sort of problems :confused: post back if you find the problem, you may help others and good luck.

---

### Post by SpaceTeddy on 2008-08-13
I have not tried knoppix yet (as it is really, really hard to setup a live cd to work as my computer does at the moment. Just trying to get the downloads to work the same day would take me half a day alone). Nonetheless, i will try this if this problem persists.

For the Fans - that is kind of a problem. This is a laptop, and i have tried multiple times to open it for cleaning - there is no way i can open this thing without breaking it. So, that is not really possible. Although, when i am in windows (usually for games) there is a lot more stress on the CPU adn GPU, and the temperatures are usually at least 10° higher than ubuntu. Windows did not crash or freeze on me (just yet) when i was gaming... 

I have already tried the logs - there is nothing in it. Ubuntu must freeze before the kernel is able to write anything to the logs. I've checked syslog, messages, kern and Xorg.*

here is a crash of ubuntu from the kern.log ( i was burning a DVD and paring my laptop with a mobile via bluetooth at the time):
```
Aug 11 12:12:13 ipoese-laptop kernel: [11588.721533] ISO 9660 Extensions: Microsoft Joliet Level 1
Aug 11 12:12:13 ipoese-laptop kernel: [11588.750833] ISOFS: changing to secondary root
Aug 11 12:35:22 ipoese-laptop kernel: [12974.975275] cdrom: This disc doesn't have any tracks I recognize!
**<-- crash here --->**
Aug 11 12:40:57 ipoese-laptop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 11 12:40:57 ipoese-laptop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 11 12:40:57 ipoese-laptop kernel: Symbols match kernel version 2.6.24.
Aug 11 12:40:57 ipoese-laptop kernel: Loaded 25333 symbols from 94 modules.

```

same time from messages:
```
Aug 11 12:12:13 ipoese-laptop kernel: [11588.687056] UDF-fs: No VRS found
Aug 11 12:32:28 ipoese-laptop -- MARK --
Aug 11 12:35:22 ipoese-laptop kernel: [12974.975275] cdrom: This disc doesn't have any tracks I recognize!
**<-- crash here --->**
Aug 11 12:40:57 ipoese-laptop syslogd 1.5.0#1ubuntu1: restart.
Aug 11 12:40:57 ipoese-laptop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 11 12:40:57 ipoese-laptop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.

```

And also syslog:
```
Aug 11 12:36:58 ipoese-laptop hcid[6013]: pin_code_request (sba=00:14:A4:8B:F3:0C, dba=00:17:83:8E:EC:2C)
Aug 11 12:37:16 ipoese-laptop hcid[6013]: Passkey agent replied with an error: org.bluez.Error.Rejected, Pairing request rejected
Aug 11 12:37:16 ipoese-laptop NetworkManager: <debug> [1218451036.717590] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_17838eec2c'). 
**<-- crash here --->**
Aug 11 12:40:57 ipoese-laptop syslogd 1.5.0#1ubuntu1: restart.
Aug 11 12:40:57 ipoese-laptop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 11 12:40:57 ipoese-laptop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
```
As you can see, the bluetooth pairing is the last that was done, the the computer just... stopped. 
Mind you, this has (most likely) nothing to do with bluetooth, as it worked right after the reboot, and i had a lot of crashes where bluetooth was not even involed in any way.

And yes, i hate this kind of problems too. but i cannot have my computer crash on me every day...

thanks for the suggestions !

---

### Post by SpaceTeddy on 2008-08-19
so i have testes some more - what is even worse, i have some results that kind of scare me. But first, i think i must explain what i am doing. 
In my total setup, there is my laptop and two servers involved. setup looks like this:

Laptop <-LAN-> Server1 <---Internet--> Server2

The crucial part here is Server2. It has 12 IP addresses assigned to itself and runs 12 separate proxies on different ports. From my Laptop i can connect via Openvpn Server 2 (directly, Server1 is not used yet) and spawn 12 different Firefox Profiles on it (my laptop). Each Firefox Profile uses one of the Proxies on Server2, thus every Firefox instance on my Laptop has a different IP-address. This was only done as a proof-of-concept, but has given me serious headaches. I'd say about 50% of the when i use this setup in combination with heavy data transfer (hey, let's download Ubuntu 12 times at the same time over 12 different ip's for the fun of it) my laptop freezes. it just dies. That i have already been explaining. 

Now - Server1. Server1 is my home Server. As i did not know if this was a hardware issue, software issue or something else in my laptop, i though of replicating the setup to server1. So that one also has a vpn connection now, it also has Firefox installed (the server is pure CLI - Firefox runs via x-forwaring on my laptop) and it has the different proxies. And here comes the scary part... i can reproduce it. If i start the download on Server1 via the proxies on Server2 - server1 crashes about 50% of the times... The Question, what is crashing it. 

I've already compared the specs... the Hardware is entirely different ! My laptop runs mainly on Intel stuff, the Server runs is a VIA barebone. No driver for the network is the same - as i said - the server does not have X installed (and when it crashes my laptop is just fine although i have the Firefox session on my screen). So, here are the differences

Laptop - Server1

Intel Hardware vs. Via Barebone
X-server vs. Pure CLI
Firefox 3.0.2 vs. Firefox 2.0.0.16 (iceweasel)
kernel 2.6.24-19-generic vs.kernel 2.6.18-6-686
openvpn 2.1_rc7 vs. openvpn 2.0.9

as far as i am aware, there is no other software used. So... does anybody have an explanation for this behavior ? Why do both computers that are totally different, crash ?

i am still... confused about it.

---

### Post by SpaceTeddy on 2008-08-27
bump... 

i am still having those issues...

---

### Post by dragos240 on 2008-08-27
> **SpaceTeddy said:**
> bump... 

i am still having those issues...
It might be becuase of ram. I'm impressed you can run all that, but, you could use an upgrade of ram. If you say that you can't open it. Tell me the model and the company:

Example: Sony vaio VGN-FS760/w.

I could find a possible way to open it.

---

### Post by yodermk on 2008-08-27
Mine freezes sometimes too. I just looked at the logs and dmesg and not much seems wrong, but I was getting some stk11xx module errors, for the Syntek webcam.  Usually mine hangs within 15 minutes or so of booting, if it does, and if it passes that it will go fine for more than a week until some other weird issues cause me to reboot. However last night it hung after a day or two of uptime.

Curious, what is the output of:
cat /proc/sys/kernel/tainted
?
If it is 0, you may have some luck asking on the linux kernel list.  If it's 1, don't even think about it.

I am using the nVidia proprietary driver :( and was thinking it might be part of my problem. It taints my kernel.

---

### Post by SpaceTeddy on 2008-08-27
> laptop:~$ cat /proc/sys/kernel/tainted
1

Ok, i don't even bother asking then... (btw - what does that tell me ?). Drivers for me is the fglrx restriced module (ATI X1600 Mobile) - and Errors - i am not getting any errors. The system dies before it can write anything. After a reboot, syslog, dmesg, kern.log... they're all empty as if nothing happened... Also, i 've turned the screensaver off on the server and deliberatly crashed it - nothing on the first console either. It just... stops... 

As for ram - this is not a ram issue. First off, i have two gigs ram already, and htop as well as the sysmon tell me that even with 12 instances of firefox open i still have over a gig of ram free. So unless it spikes real fast, this is not the cause of it... And i know what kind of ram i need - but the laptop is maxed out (i think) at 2 Gbyte... BTW, it's a Samsung X60 student edition (it's not listed in on the sasmung site) - the closest you get to it is the Samsung X60 Becudo.

[EDIT]
here are the processes, memory and cpu usage during a multi ip download:

> laptop:~$ mpstat 
Linux 2.6.24-19-generic (laptop) 	27.08.2008

21:22:49     CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
21:22:49     all    9,87    0,13    2,62   11,58    0,49    0,22    0,00   75,08    569,76
ubuntu@laptop:~$ ps aux |grep firefox
ubuntu    6947  2.6  4.2 208752 87408 ?        Sl   21:00   0:35 /usr/lib/firefox-3.0.1/firefox [http://ubuntuforums.org/showthread.php?t=883001&goto=newpost](http://ubuntuforums.org/showthread.php?t=883001&goto=newpost)
ubuntu    7492  0.8  2.1 128960 44244 pts/0    Sl   21:10   0:05 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 165 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    7508  0.8  2.1 121036 44356 pts/0    Sl   21:10   0:06 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 166 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    7517  0.8  2.1 129708 45304 pts/0    Sl   21:10   0:05 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 167 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    7529  0.8  2.1 129672 45584 pts/0    Sl   21:11   0:05 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 168 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    7541  0.8  2.1 129352 44920 pts/0    Sl   21:11   0:06 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 169 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    7556  0.8  2.1 129244 44812 pts/0    Sl   21:11   0:05 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 170 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    7560  0.8  2.1 129512 44632 pts/0    Sl   21:11   0:05 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 171 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    7579  0.8  2.1 129340 45004 pts/0    Sl   21:11   0:05 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 172 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    7588  0.9  2.4 134652 50336 pts/0    Sl   21:11   0:06 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 173 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    7600  0.9  3.2 151196 66380 pts/0    Sl   21:11   0:06 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 174 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    7619  0.8  3.3 146512 70040 pts/0    Sl   21:11   0:06 /usr/lib/firefox-3.0.1/firefox --height 1000 --width 600 -P 175 -no-remote [ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](ftp://ftp.fu-berlin.de/linux/ubuntu/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
ubuntu    8518  0.0  0.0   3016   788 pts/1    R+   21:22   0:00 grep firefox
ubuntu@laptop:~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          2025       1922        102          0         31       1066
-/+ buffers/cache:        824       1200
Swap:          941          0        941


And yes - even with the kernel update from today, it still crashes...

---

