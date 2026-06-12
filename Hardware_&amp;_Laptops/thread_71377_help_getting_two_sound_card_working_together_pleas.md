---
title: "help getting two sound card working together please."
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by sal on 2005-10-03
im trying to get my two sound cards to work together in the following configuration:
sound card 1 (on-board - intergrated on motherboard) :
use this card for recording audio from its microphone jack.

sound card 2 ( on pci slot of motherboard) : use this card as the device from wich sound comes from (connect speakers to)

here is the releveant info from lspci:
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01) <=== intergrated sound
0000:01:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS <=== PCI add in card

here is the info from an lsmod |grep snd:
snd_ca0106             30916  1
snd_intel8x0           33248  1
snd_ac97_codec         83932  2 snd_ca0106,snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  4 snd_ca0106,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  11 snd_ca0106,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  3 snd_ca0106,snd_intel8x0,snd_pcm

now here is my asound.conf:
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

what would i have to do to make the sound blaster play audio and the intel intergrated sound record audio? 
I'm using Kubuntu 5.10 Breezy
I have confermed that the intergrated and the sound blaster both work to give off the sound, but from my research found that the sound blaster card will not be able to use a mic becuase from what i read it will not be untill alsa 1.10 that the sound blaster card will support a mic, so i want to be able to use the suond blaster card for listining to sound, and the intergrated intel sound to record. i currently have the intergrated in use and can conferm that i can record with it and use it with skype. 
anyone that can help thanks in advance, sorry this thread is so long.
thanks.

---

