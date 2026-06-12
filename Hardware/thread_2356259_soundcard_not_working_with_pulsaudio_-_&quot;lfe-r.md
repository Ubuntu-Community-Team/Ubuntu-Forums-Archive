---
title: "soundcard not working with pulsaudio - &quot;lfe-remixing&quot;"
date: 2017-03-21
forum: Hardware
---

### Post by 7zehnerdeckel on 2017-03-21
Hello,  
I use a 2.0 audio-system with additional active subwoofer (so now 2.1) on my  [PC with 5.1 audio output]("http://www.asrock.com/mb/Intel/Z87E-ITX/index.de.asp") (green jack plug for stereo, orange for suboofer).
So that the subwoofer is synonymous with stereosources, I  have activated in the "daemon.conf" of Pulseaudio (under / etc / pulse  /) lfe-remixing, set the crosover frequency, specify the number of  loudspeakers and define the loudspeaker:  
```

Enable-lfe-remixing = yes 
Lfe-crosover-frq = 80 
default-sample-chanels = 3 
default-chanel-map = front-left, front-right, lfe 

```
Unfortunately, the subwoofer not working!  :-( 
If  "enable remixing" are aktiv (default is active):  
```
Enable remixing = yes 
```
the subwoofer will work for a few programs such as Audacius or  GNOME MPlayer (regardless of "enable-lfe-remixing" are enabled  or disabled!), but still not wor at my "what to use programm" Kodi.  
Does anyone know what I do wrong? 
I have exactly  used this configuration  before at Debian Jessie with Pulsaudio 7.1 (without enable remixing)  and there the subwoofer has worked with every program.  :-k

Sundchip:
```
[B]
[pat@Server ~]# head -n 1 /proc/asound/card1/codec*[/B] 
Codec: Realtek ALC1150
```
Greetings, H.

---

