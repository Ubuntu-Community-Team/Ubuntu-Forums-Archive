---
title: "Another Hoary Sound Issue (I tried to other solutions!)"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by nehalem on 2005-03-25
Hi all,
I'm the same as many people, it seems to be an issue with /dev/dsp and it prevents certain applications from using sound such as the battle of wesnoth.

I've tried loading the pcm oss module thing in /etc/modules and I've tried changing the esd server as stated in the wiki.  No luck, when I load this game (which I'm using as a test) it can't find the audio.  

So from the command line I'll type wesnoth all day and no sound.  Then when I use this statement "ls /dev/dsp /dev/mixer -l" and then type "wesnoth" sometimes I will get sounds. 

I'm clueless and not even sure if there is a connection there.

On a side note maybe the esd changes didn't do anything because I installed polypaudio (which has been nice).

Any help is appreciated.

---

### Post by teumima on 2005-03-26
try turning off the system sounds and see if it still messes up.

---

