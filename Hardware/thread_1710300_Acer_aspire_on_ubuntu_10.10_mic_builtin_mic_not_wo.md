---
title: "Acer aspire on ubuntu 10.10 mic builtin mic not working?HELP"
date: 2011-03-19
forum: Hardware
---

### Post by nsk tacticzz on 2011-03-19
Hey guys my mic thats prebuilt into my netbook wont record on any programme also like omegle and skype dont work cause my mic please help. i've gone to alsamixer and turned everything up and unmute but it still wont work please help

---

### Post by dougalkerr on 2011-03-27
I have the same problem on my wife's brand new Aspire One. She needs the internal mic working for when she is away and for the life of me I can't get it to work with Skype. I have had it recording in sound recorder so I know it works.
Why is Skype such a pain when it comes to simple things...
Oh well if anyone knows what we need to do please help. It sounds like a lot of people are pulling their hair out over  what should be a simple fix.

Cheers,

---

### Post by PARO on 2011-03-31
my gateway netbook has the same problem, the simplest solution would be to uninstall pulse audio. and it's not just a skype problem, no sip clients work for me under pulse now (they worked fine under lucid though,so this is a new problem... maybe we should file a bug report?)

---

### Post by PARO on 2011-03-31
A less simple solution that will let you keep pulseaudio is to tinker with the alsa controls for the mic. I was able to get it working by installing gnome-alsa-mixer and moving the mic to a max audio level of about 75% you can still move the mic boost all the way up if you want it louder though. You can also tinker with this directly when in Ekiga (if you use Ekiga also). This will let you keep pulseaudio... Hooray! still looks like a bug though...

---

