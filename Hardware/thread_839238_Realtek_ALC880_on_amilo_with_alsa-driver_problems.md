---
title: "Realtek ALC880 on amilo with alsa-driver problems"
date: 2008-06-24
forum: Hardware
---

### Post by Imaculent on 2008-06-24
Hello!

I've been googleing(?) and reading a lot and my problem is a bit different from all the others I've read...

Fujitsu Amilo M3438G with Realtek ALC880. Runs Ubuntu 8.04.

I added: 
"options snd-hda-intel model=fujitsu"
in
"sudo gedit /etc/modprobe.d/alsa-base"

and everything got much better! I can adjust volume on the internal speakers and headset, the external volume button works and the internal mic works.
The internal speakers and mic is being silenced when plugging in a headset.
The headphones works perfect, i can adjust their volume individually.
So far so good...

The problem is that the headset mic doesn't work. :(
First I thought that the contact or the mic itself was broken but tests in Windows shows that it isn't.

Anyone got any idea? Would be very grateful for any help. This is really messing up my Ubuntu-using.

/
Kenneth

---

### Post by xadpc on 2008-09-15
I have the same laptop and can't even get the internal mic to work. :(

Did you do anything else besides that? I have installed Realtek drivers from their site.

---

