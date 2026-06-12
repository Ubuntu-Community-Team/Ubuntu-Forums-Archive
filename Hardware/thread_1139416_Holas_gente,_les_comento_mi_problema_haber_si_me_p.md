---
title: "Holas gente, les comento mi problema haber si me pueden ayudar...en general no pido a"
date: 2009-04-27
forum: Hardware
---

### Post by sefsinalas on 2009-04-27
[Imagen y Sonido]("http://www.ubuntu-es.org/?q=forum/49")     Holas gente, les comento mi problema haber si me pueden ayudar...en general no pido ayuda pero este problema lo he tenido desde siempre en linux con todas mis pcs.
Tengo **ubuntu 9.04 de 64 bits** y lo que quiero hacer es realizar llamadas de pc a pc y lo quiero hacer usando empathy o cualquiera que permita conectarse usando gtalk.Pero hasta ahora he googleado como 5 hs y no he encontrado la solucion al problema de que "el otro" no me escucha lo que digo por el micro....ni siquera puedo grabar algo con el grabador de sonido del ubuntu...nada.
**Mi mother es una ASUS M2N-MX SE**

 el comando lspci | grep -i audio me tira esto:
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)


 el comando lsmod | grep -i snd me tira esto
snd_hda_intel         557364  5
snd_pcm_oss            52352  0
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0
snd_seq_oss            41984  0
snd_seq_midi           15744  0
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 78792 18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
 No se imaginan como les agradeceria su ayuda ya que no encuentro ninguna solucion [IMG]http://www.ubuntu-es.org/misc/smileys/sad.png[/IMG]

---

