---
title: "Sound Blaster Live! 24 bit : ca0106 module probs :/"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by HeadUp on 2005-06-27
Hi!
I think we can say i'm a newbie in linux world, just a little experience....

So I got a SBlive 24bit!, I follow step by step this thread : [http://www.ubuntuforums.org/showthread.php?t=19307](http://www.ubuntuforums.org/showthread.php?t=19307) and I got sound, but no microphone.
Alsamixer shows me only 8 or 9 different volumes level, and no input (or only one called capture ??!?).

I need Teamspeak and Enemy territory working in the same time, it's the last way to makes me removing Windows. 

Please help me I won't give up Linux, and I wanna avoid Windows.

---

### Post by kmail on 2005-08-26
i have 100% same problem, and i also have a choppy sound output with XMMS usin the alsa output plugin, thats not a problem though, because OSS plugin works just fine, but i also am interested in getteing my mic work and sound from teamspeak and enemy territory working at the same time. Atm only one program can use the soundcard at a time.

---

### Post by sidd-tx on 2005-08-31
As far as the choppy sound,,, I had the same problem with my Sound Blaster Live! 24-bit soundcard. I used the following fix:

[http://www.ubuntuforums.org/showthread.php?t=21211](http://www.ubuntuforums.org/showthread.php?t=21211)

but I took the "--with-cards=emu10k1" out of the configure. 

And put "snd-SB0410P17" instead of "emu10k1" into /etc/modules...  

I still haven't gotten my mic to work though. So if you get yours working,, help a brutha out....

Sidd...

---

