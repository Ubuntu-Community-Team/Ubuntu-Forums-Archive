---
title: "Acer Aspire 5738g surround problem."
date: 2011-08-08
forum: Hardware
---

### Post by dhtj on 2011-08-08
Hi all.
I have Acer Aspire 5738G.
My Ubuntu version is Natty, but i have the same problem in the older versions.
My sound card is Realtek ALC888 with 3 plugs. On windows it hads 4 modes:
   1. 2chanel with LineOut, LineIn and MicIn
   2. 4chanel with LineOut(front) LineOut2(Rear) and MicIn
   3. and 4. are not on this topic now...

When i switch to mode number 2 , LineIn becomes LineOut for the rear speakers. This was on windows (7).

On Ubuntu i have only 2 chanel option. One dude from Bulgarian unofficial ubuntu forums told me to edit this file ***/etc/modprobe.d/alsa-base.conf*** and to add to its end this:
```
options snd-hda-intel model=8930g
```
* *8930G is laptop with sound card like mine.*
After editing the file and restarting, I have more options in Sound menu, like 4.0 ; 5.1 and so on.
[[img]http://store.picbg.net/thumb/D3/46/62315a5f960ad346.jpg[/img]](http://picbg.net/img.php?file=62315a5f960ad346.jpg)

But the problem is, there on the photo writes in bulgarian language "one input/one output" , but I need two outputs. With this setup i have sound only in my front speakers, which is connected to my default LineOut. I tried to connect my rear speakers to LineIn and MicIn, but there's no output signal. Can you help me?

---

### Post by dhtj on 2011-08-09
*bump*
:popcorn:

---

### Post by dhtj on 2011-08-10
I found the solution: [http://ubuntuforums.org/showthread.php?t=1431003](http://ubuntuforums.org/showthread.php?t=1431003)
Sorry for posting.

---

