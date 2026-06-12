---
title: "C-Media 9738"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by dJnEvS on 2005-08-31
I need some help with my surround sound system..
my rear speakers doesnt work (no, they arn't broken ;) :P )
i turned Line in as Surround on, but still nothing..

---

### Post by Lord Illidan on 2005-08-31
Is there an option for Line Out Surround?

Also, I think, apps such as Xine (viewing DVDs) may have good surround sound, you just need to enable it in "Settings"..

---

### Post by dJnEvS on 2005-08-31
ok, i put the surround thing on 5.1 but still, no rear..

---

### Post by Lord Illidan on 2005-08-31
So, correct me if I am wrong...

When watching movies which have surround sound in Xine, with 5.1 surround enabled, you still don't have Surround Sound..

Is the sound card integrated (ie, on the motherboard) or a  seperate sound card?

This might not help much, but C-Media are not renowned for driver support (My cheapo 8738 C-media card doesn't work under Windows XP.. but works somewhat under Ubuntu, though I don't care for Surround Sound)..

Try this site anyway.. [http://gentoo-wiki.com/HOWTO_Surround_Sound](http://gentoo-wiki.com/HOWTO_Surround_Sound) .

It is for Gentoo but you should understand what is going on..

---

### Post by dJnEvS on 2005-09-01
wierd, but when im trying to do:
```
# aplay -Dsurround foo.wav
```
i get this error:
```
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM surround
```
and a file not found..
in m$ wnidoos i need a codec or something to apply the surround, dont i need that in linux?

---

### Post by Lord Illidan on 2005-09-01
What's the codec?

It's not the fault of Linux that the surround is not working.. C-media's crappy drivers are well known, just do a google search..

---

### Post by dJnEvS on 2005-09-01
lol, ic what i did wrong,
i typed -Dsurround in stead of -Dsurround51
but nou he just cant find the file..
so cant play it.

the codec or whatever it is, autmatticly install with the drivers setup..
i get a trayicon, where i can select if im using headphones, 2 speakers or 4...
and some other shit to make the sound 'better'

---

### Post by Lord Illidan on 2005-09-01
[QUOTE=dJnEvS]lol, ic what i did wrong,
i typed -Dsurround in stead of -Dsurround51
but nou he just cant find the file..
so cant play it.[/QUOTE]

Of course, if there is no foo.wav.. 
Try playing an mp3...

---

### Post by dJnEvS on 2005-09-01
```
# aplay -Dsurround51 "/home/sven/Muziek/John Miles - Music was my first love.mp3"
Playing raw data '/home/sven/Muziek/John Miles - Music was my first love.mp3' : Unsigned 8 bit, Rate 8000 Hz, Mono
aplay: set_params:835: Broken configuration for this PCM: no configurations available

```

---

### Post by Lord Illidan on 2005-09-01
Try setting the pcm in alsamixer...

Are there any more knowledgeable guys who can help this guy out? I have reached the limit of my knowledge regarding surround sound and Ubuntu...

---

### Post by dJnEvS on 2005-09-01
ok, thanks for your help so var :)

---

### Post by dJnEvS on 2005-09-01
[QUOTE=Lord Illidan]Try setting the pcm in alsamixer...

Are there any more knowledgeable guys who can help this guy out? I have reached the limit of my knowledge regarding surround sound and Ubuntu...[/QUOTE]
 bump

---

