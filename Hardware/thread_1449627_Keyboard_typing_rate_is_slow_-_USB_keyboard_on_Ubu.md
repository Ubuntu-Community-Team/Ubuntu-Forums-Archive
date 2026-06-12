---
title: "Keyboard typing rate is slow - USB keyboard on Ubuntu 9.04"
date: 2010-04-08
forum: Hardware
---

### Post by ekawahyu on 2010-04-08
I have an Artigo A1000 machine with C7 1 GHz and 1 GB of RAM. Ubuntu 9.04 runs pretty fast on this machine 40 second of booting time, however I encountered a very slow keyboard typing rate. I didn't open any program yet, but system monitor said that my CPU usage is already 100%. I have only USB port on this machine so I could not try to experiment with PS/2 keyboard on it.

At the beginning I thought it was something hogging the system. I started to disable some services and managed to reach up to 40% of CPU usage only. I open terminal and firefox, nothing has changed. The typing rate is still slow. I mean really slow like you I could type only 1 letter for each second.

By mistake, I open youtube, movie player, rhythmbox and while the video and the mp3 music is playing, I could get a normal typing rate on my keyboard. I checked system monitor it says 80% of cpu usage. So, it was not something that hogging the system. It is probably a bug somewhere in the setting.

My curiosity grew and I put back all disabled services. I played a video or MP3 music, and I could get a normal typing rate without problem. System monitor says 100% of CPU usage, but I don't think this matters since everything works normal. But when I stopped the video or the music, I got the slow typing rate again. There is something that I don't understand here, where am I doing wrong?

By the way, the solution for now is repeatedly playing MP3 music while typing whenever I start Ubuntu. Everytime I need to type a document using OpenOffice, I have to play some music :) A neat solution but I hope somebody could explain and fix this problem for me. Thanks.

---

### Post by ekawahyu on 2010-04-24
I guess I solved the problem. Just by enabling the APIC in BIOS and everything works fine now.

---

