---
title: "HDMI Audio / Alsa : no more sound, no more output card in gnome-control-panel"
date: 2010-11-05
forum: Hardware
---

### Post by Socap on 2010-11-05
Hello,

I have a nVidia ION 2 platform on my Shuttle XS35GT. Sound output is set on HDMI via alsa, and everything was working fine until today's package updates. Honestly, I don't know what was the content of these updates, neither do I know if i can get back to my old - and working - configuration.

I'm running Lucid Lynx, with alsa 1.0.23.

In fact, I can ouput some sound with aplay if I specify the output to plughw:1,7. But here is the problem :
- No application will play any sound (tried vlc & rythmbox)
- gnome-control-panel crashes if I want to "test my speakers" on my "High definition audio controller"
- In the output cards section of gnome-control-panel, I just have "dummy output"

Below is some information you might find useful. I will provide more if you have any suggestions that might lead to a solution...

```
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfcffc000 irq 43
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe97c000 irq 17

``````
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

``````
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

``````
$ cat /etc/asound.conf 
pcm.hdminvidia {
   type plughw
    card 1
    device 7
}
pcm.!default hdminvidia

```Extract from /usr/share/alsa/alsa.conf :

```
defaults.ctl.card 1
defaults.pcm.card 1
defaults.pcm.device

```Thanks in advance for your precious help. I'm not an advanced user, and I'm lost here. Having a working conf one day, then nothing, is a bit frustrating. As I'm french, you'll also hopefully excuse my limited knowledge of english :)

---

