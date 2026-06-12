---
title: "[SOLVED] Ubuntu 7.10: Sound disappeared on installing alsa 1.0.15 on Sony Vaio VGN-NR"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by pranami on 2007-12-30
Dear Ubuntu users,

       Being that I fervently support the "open source" and "free" philosophy of Ubuntu :guitar: I wanted to convert to Ubuntu user from Mac and Windows user. So, I installed Ubuntu 7.10 on my laptop Sony Vaio VGN-NR110E which I bought on Black Friday at Best Buy (Yes, I did it ... it was madness but I did it). I had to work a bit and go ndiswrapper route to get the wireless internet working, I installed codecs for DVDs and mp3. "Fn" keys still did not work but I didn't care because I can change the screen brightness using xbacklight. At this point I was in love with my laptop with Ubuntu on it.:D

       Sound was working but when I connected headphones sound was coming from both the headphones and external speakers. I knew that being greedy is not good thing but I got greedy :icon_frown: and tried to fix this issue by installing new version of alsa 1.0.15. Unfortunately for me that did not go well and now the sound on my laptop disappeared completely. Along with greedy I was stupid ](*,) ... I did not document what I did ;(. So after messing things up, I tried to reinstall the older alsa 1.0.14 using synaptic package manager but that further screwed up my laptop. Now when I started Ubuntu a command prompt appears!! No GUI :( I had to type "startx" to get it to work and then I reinstalled GNOME desktop which fixed this problem of "no GUI". Here are the commands I used ([credit to: Leo the Lion]("http://ubuntuforums.org/showthread.php?t=608767&page=4")=D>):

sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start

      Unfortunately for me, doing so did not fix the sound problem. Ubuntu is not able to detect the sound card at all :confused:. The directory /proc/asound/cards is empty. 

pranami@G-Crib:~$ cat /proc/asound/cards 
--- no soundcards ---

pranami@G-Crib:~$ aplay --list-devices
aplay: device_list:204: no soundcards found...

     The output of the command "lspci -vvnn" contains:

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
        Subsystem: Sony Corporation Unknown device [104d:902d]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

      Please help me resolve this issue. I am anxiously waiting for cues to fix my beloved Ubuntu :-({|=, Your help is greatly appreciated. I am holding my heart in my hand and looking for someone to help me.

Thanks

---

### Post by murmel on 2007-12-30
Check out [this](http://ubuntuforums.org/showthread.php?t=650790) thread, it's for Sony Vaio VGN-CR21* but the the sound card installation propably works for NR to.. Try it out!

---

### Post by pranami on 2007-12-31
> **murmel said:**
> Check out [this](http://ubuntuforums.org/showthread.php?t=650790) thread, it's for Sony Vaio VGN-CR21* but the the sound card installation propably works for NR to.. Try it out!

 Tip of the hat to you sir murmel =D>. Your suggestion worked for me beautifully :) . Thanks a lot.

---

