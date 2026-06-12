---
title: "No mic since update to 2.6.35-24-generic"
date: 2011-02-06
forum: Hardware
---

### Post by fa.oliehoek on 2011-02-06
Hi,

My microphone has stopped working since  2.6.35-24-generic ('24') (x86_64). I.e., it works on 2.6.35-23-generic ('23') and earlier but not anymore.

My sound card is a Realtek ALC275 (laptop is VAIO F12SGX). When I compare the gnome-alsamixer panel between the mentioned kernel numbers, there is a striking difference:

Under '23' I have a column named 'capture' and a check box under it 'rec'.
Under '24' this column and check box do not show up.

So, it seems as if my soundcard is not detected properly anymore?

When initially switching to 10.10 (from 10.04) I had to add
options snd-hda-intel model=3stack
to /etc/modprobe.d/alsa-base.conf, to be able to select duplex. By now, this line does not seems to have any effect anymore (so I removed it). 

Summarizing: my card is listed as duplex, and all the software settings should be ok (I think). It is just that my card is not detected properly anymore? Any ideas?

Thanks!

---

### Post by fa.oliehoek on 2011-03-01
Does nobody have a clue? The new kernel '-27' also does not fix the problem...
(2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux)

Well, I guess I'll keep using the old version.

---

