---
title: "Can you use firewire for a primary audio device?"
date: 2011-03-04
forum: Hardware
---

### Post by Raikonex on 2011-03-04
I've been doing a bunch of googling and can't seem to find anything on how to set up a firewire audio system to be the primary sound device in ubuntu. I have a windows pc as my main system and I use a presonus FP10 as the sound device. The built in soundcard sounds like crap especially on my studio monitors. I'd like to have everything go through my firewire system like youtube and my music player to get really good sound quality like I can in windows.

Also, I don't want to use Ubuntu Studio as I'm going to be using my computer for more than just studio work. The wifi support on it is also terrible and completely non-existent with my hardware setup when I'm using Ubuntu Studio.

Any help would be greatly appreciated :)

EDIT: I upgraded Ubuntu 10.04 to Ubuntu Studio which seems to have fixed the wifi problem

---

### Post by Hedgehog1 on 2011-03-05
Welcome Raikonex!

Do you know I have been using firewire for years as a DV transport, and never even knew it could feed sound to an external device to replace your card until I read your post?

So, here is what I found:

*The FFADO project aims to provide a generic, open-source solution for the support of FireWire based audio devices for the Linux platform.*  Link: [http://www.ffado.org/]("http://www.ffado.org/")

A post in our own forums about this: [http://ubuntuforums.org/showthread.php?t=739839]("http://ubuntuforums.org/showthread.php?t=739839").  They talk about using FreeBob, which has since been replaced by FFADO.

But data is rather scarce on this subject, I have to agree.

I hope the FFADO project has what you need.  It appears to be the only game in town at the moment. 

***The Hedge***

:KS

---

### Post by cchhrriiss121212 on 2011-03-05
You can but it needs some set up. Once you have the device working with jack using the FFADO driver, you then need to route ALSA through jack. See here:
[http://www.alsa-project.org/main/index.php/Asoundrc#JACK_plugin](http://www.alsa-project.org/main/index.php/Asoundrc#JACK_plugin)

---

### Post by Raikonex on 2011-03-05
I was starting to think that maybe this was something that was impossible to do at the moment but thanks, I will definitely give that a try

---

### Post by Raikonex on 2011-03-12
Could someone possibly help me route alsa through Jack and get all my programs and stuff outputting their audio through alsa? I have my FP10 working properly with Jack but I'm a little lost. I have no clue where to even start next.

---

### Post by peladovii on 2011-03-13
Ive just sent you a PM.

I think the key is in the link that cchhrriiss121212 provided.

but im kinda lost there.

This whole firewire thing has separated me from linux from 2 years- i hope we can find a way for this :D

---

### Post by cchhrriiss121212 on 2011-03-13
You need to open up a text editor, then paste in the text shown in the link above, save the file as .asoundrc in your home folder.
After that, start jack and then open up an ALSA only program, you should see it automatically connect to your outputs via jack.

Edit, some more tips here:
[http://ubuntuforums.org/showthread.php?t=1571408](http://ubuntuforums.org/showthread.php?t=1571408)

---

### Post by Raikonex on 2011-03-13
I've created and edited .asoundrc to look like this:
```

pcm.!default {
           type jack
    playback_ports {
           0 alsa_pcm:playback_1
           1 alsa_pcm:playback_2
       }
    capture_ports {
           0 alsa_pcm:capture_1
        1 alsa_pcm:capture_2
    }
}
```But so far nothing seems to work. Jack runs fine but nothing from Alsa is going into it.

---

### Post by peladovii on 2011-03-14
Same here,

0 alsa_pcm:playback_1
1 alsa_pcm:playback_2

Aren't qe suppose to rename "playback_X" to the correspondent name of the card?

Im in the office right now but i recall my outputs named like "00123457895MainOutputL" etc

there is a command to show outputs and inputs, unfortunately I can't remeber it right now

---

### Post by cchhrriiss121212 on 2011-03-14
1 and 2 should work fine, they are the names for the first 2 channels on any card using jack. 

The only reason I can think of why this won't work, would be due to pulse audio (I can't test this as I don't have pulse on my system).
Try disabling pulse like this:
[http://ubuntuforums.org/showpost.php?p=9555029&postcount=4](http://ubuntuforums.org/showpost.php?p=9555029&postcount=4)

If it works you could remove pulse, there is no point having it anyway if you want to run all your sound through jack.

---

### Post by Raikonex on 2011-03-14
Well I had things working earlier by managing to route pulse audio into Jack...but that seemed to cause a bunch of problems such as random lock ups and crashes. So I undid everything I did, and completely uninstalled pulse audio. No more crashes or lock ups, but I'm not getting any alsa audio going through jack either...hmm

---

### Post by peladovii on 2011-03-14
Thanks for your replies!, im gonna try that as soon as i get home. 

Regards.

How do u unninstall completely pulseaudio? Im kinda new at linux, well never use it as I got no sound :P

---

### Post by peladovii on 2011-03-16
> **Raikonex said:**
> Well I had things working earlier by managing to route pulse audio into Jack...but that seemed to cause a bunch of problems such as random lock ups and crashes. So I undid everything I did, and completely uninstalled pulse audio. No more crashes or lock ups, but I'm not getting any alsa audio going through jack either...hmm

Same here, File .asndrec doesn't seem to do anything at all. I managed to install module-jack-source and module-jack-sink to route pulseaudio through JACK but with some system inestability unfortunately.

---

### Post by cchhrriiss121212 on 2011-03-16
> Same here, File .asndrec doesn't seem to do anything at all. 
I'm not sure if that was a typo, but it is supposed to be:
.asoundrc

And it must go in your /home/username folder.

---

### Post by peladovii on 2011-03-16
> **cchhrriiss121212 said:**
> I'm not sure if that was a typo, but it is supposed to be:
.asoundrc

And it must go in your /home/username folder.

Indeed, was a typo, sorry.

I will double check its destination and name back home. 

Thanks Chrisss!

---

