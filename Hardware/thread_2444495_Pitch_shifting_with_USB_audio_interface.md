---
title: "Pitch shifting with USB audio interface"
date: 2020-05-31
forum: Hardware
---

### Post by jthistl3 on 2020-05-31
Sometimes with my Behringer UMC202HD interface, the pitch of some  things will be shifted down. This often happens when I start a game -  for example, starting X-Plane will *always* result in this  happening, and the pitch of everything in the system will be shifted  down. Skype sometimes also does this. Often I can fix the problem by  simply unplugging the interface and then plugging it back in.


  With other things, however, the problem is more subtle and not  fixable in a reproducible way. With the Witcher 3, for example, the  dialogue only (not the music!) is pitch shifted down. This is noticeable  because the dialogue lines consistently get cut off suddenly before  they end. I don't know what might cause this - I have VSync turned off,  and a constant 60fps.


  FWIW, I'm using Pulseaudio. I don't have any custom configurations  set up as far as I'm aware. This is as really disconcerting problem that  I've been struggling to find a solution for a for a while, so any help  is very much appreciated.


  I'm running Ubuntu 20.04 LTS, but I also have this problem on my 18.04.3 laptop.

---

### Post by CatKiller on 2020-05-31
I could see a sample rate mismatch having that effect. That's where I'd look first. PulseAudio has some options for default sample rates and resampling.

---

### Post by jthistl3 on 2020-05-31
Hmmm, I found some stuff related to that but nothing that solves it. Then, I tried starting up Pavucontrol, which itself caused a pitch shift. I then restarted Pulseaudio, and the pitch was corrected. Keeping Pavucontrol open, I could start other applications without pitch shifting!

---

