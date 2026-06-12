---
title: "Choppy sound on Toshiba Portege R500 with Ubuntu 9.10 when I do something"
date: 2010-01-19
forum: Hardware
---

### Post by k999 on 2010-01-19
Hi,

I have a quite fresh install of Ubuntu 9.10 on my Toshiba Portege R500 laptop. The audio hardware is, according to lspci:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

One of the first things I did when setting up my computer was to install Spotify under Wine. It worked (after reading others' experiences here on ubuntuforums), but the music gets choppy (sounds more like a helicopter than music) every once in a while, for a few seconds, or until I change song. It especially starts chopping when I change desktop or load a new webpage or something like that.

So I gave that up, and tried playing my own mp3s with Rhythmbox instead. Then I noticed that Rhythmbox also skips when I do stuff, like change desktop, launch Terminal, or start other software, etc - but then it's just one or two chops before it continues. 

Perhaps this is a generic problem on my laptop, probably something to do with buffer underruns or something...? I actually also notice that the keyboard sometimes is slow to respond. I didn't have that problem before I installed Ubuntu this weekend. Not sure it's related, though.

So some options could be:

1. Tune ALSA buffer size?
2. Tune generic response on my laptop (scheduler?)
3. Other tunable bits and bobs?

I'd appreciate any suggestions for how to fix this. :-) But I'd also trying to keep power consumption on my laptop a bit down. It actually gets way hotter when I run Ubuntu than when I used to run Windows XP :/

---

### Post by qrwe on 2010-01-26
I got just an hour ago in another thread here at ubuntuforums which works perfectly! It was simply like this:
[LIST]
[*]Go into wine config
[*]Go to the Audio tab
[*]Uncheck ALSA and click Apply
[*]Check EsounD Driver. Click OK.
[*]Start/Restart Spotify. Enjoy! :-)
[/LIST]

---

