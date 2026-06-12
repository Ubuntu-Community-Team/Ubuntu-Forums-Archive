---
title: "how to direct sound to ext speakers?"
date: 2009-05-11
forum: Hardware
---

### Post by pdc on 2009-05-11
I am using a variant of Ubuntu; in Firefox, the YouTube video clips play the sound to the ext speakers, that come from the sound out socket on the motherboard;**the sound is excellent**

when I select a video mpeg clip; and select Mplayer; it directs the sound to the small speakers on the LCD monitor; (*I get no sound from the ext speakers*)

could anyone please advise me how to direct the sound; with mplayer; to the ext speakers; as Firefox has already chosen to do; 

many thanks

---

### Post by Dark_Stang on 2009-05-11
First, why have both cables hooked up in the first place if you only want sound out of one? That just doesn't make sense.
Second, System > Preferences > Sound.

---

### Post by pdc on 2009-05-11
> *First, why have both cables hooked up in the first place if you only want sound out of one? That just doesn't make sense*.

thanks Dark_Stang; that's a really good question:


............ **I have only one intended output** (to the ext speakers)

I realise now that the output is being directed to a small handset that we use for Skype; 

(I could not localise it before);

each of the options in Sound preferences are set to "autodetect"

and selecting any of the options; (that is not USB) does not make any test sounds appear

---

### Post by pdc on 2009-05-13
I joined the PulseAudio forum, and a member of that group kindly gave me the answer;

I opened pavucontrol: I did this by terminal, but MENU: SOUND & VIDEO: PULSEAUDIO CONTROL; gets one to the same control:

the KEY thing I learned was: the stream that you want to re-direct: **MUST BE RUNNING** for  you to change it;

1)  open PulseAudio Volume Control;
2) Click on Playback: it will say "No application is currently playing audio";
3) Start the video .......... for me, an MPEG on Mplayer;
4) return to the PlayBack tab on the PulseAudio Volume Control; it now displays audio stream;
5) right-click on the audio stream: it showed for me: two audio streams: USB and front; (for me, ext speakers)
6) I selected front, and re-directed the sound to the ext speakers

I was very appreciative of the prompt response from a member of the PulseAudio forum; 

I hope this may be of help to others

---

