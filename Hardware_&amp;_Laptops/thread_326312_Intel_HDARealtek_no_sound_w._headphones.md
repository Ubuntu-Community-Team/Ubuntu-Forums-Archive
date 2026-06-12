---
title: "Intel HDA/Realtek no sound w. headphones"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by Beliar on 2006-12-27
Hi folks,
I have Sound with my Notebook speakers, but when I plugin my Headphone I have no sound :(
I had this Problem before and solved it in Dapper, but I forgot how :(

I tried the Realtek driver and installed it with the install script and by hand (./configure, make, make install). But it didnt work...
The last time, I also added something to some config file, but I forgot what and where x|

So now I installed the latest Alsa driver from alsa-project (1.13 i think). But it didnt solve my problem :/

I foudn a lot of threads and pages, but I think there are different chips behind the intel hda codec and there are different problems. So I didnt find anything that matches my problem.
If I recall correctly, I have a Realtek 880 chip.

Thanks in advance,
Greets, Beliar

---

### Post by Beliar on 2006-12-27
Actually I looked around, and I saw on differen Screenshots and in different descriptions, that there should be a control 'Headphone' in alsamixer. But I dont have one o0

---

### Post by pseudonym on 2006-12-27
Are you plugging your headphones into a special headphone jack? This might sound obvious, but you could try plugging them into where you have your speakers plugged in (line out, presumably)...

i'd like to ask you about that realtek driver, though. My onboard sound uses an 883 chip. I thought about compiling the realtek driver to see if there was any difference in quality betwwen it and the alsa that ubuntu ships with. But when I browsed through the realtek archive it looked like it was just a source package for a slightly older version of alsa. Is this true? I couldn't find anything in it that said what the module name would be once you build it. Is it something other than snd-hda-intel?...

Thanks.

---

### Post by Beliar on 2006-12-27
Well thank you for your reply.

Because this is a Notebook, I dont have the speakers plugged in anywhere. I was talking about the integrated Notebook speakers. The Line-out is the only one, and Im sure i plugged it into the right one.
This could be caused by a bug, or because there is a control for headphones, which is not accessible and muted.

Hm I'm not sure about the Realtek driver. I guess its an Alsa which was patched. o0

---

### Post by Beliar on 2006-12-28
*push*

No ideas? :(

---

### Post by Beliar on 2007-04-26
Oh, forgot to say that its solved.
I just had to edti /etc/modprobe.d/alsa-base and add this option at the end:

options snd-hda-intel model=z71v position_fix=1

EDIT:
hmm, is there no way to add [SOLVED] to the title :/

EDIT2:
OK, found it, its behind the "Go Advanced" button, thats too hidden x|

---

