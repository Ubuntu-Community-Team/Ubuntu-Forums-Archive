---
title: "Toshiba Tecra A8 - no sound."
date: 2011-08-17
forum: Hardware
---

### Post by originalchoice on 2011-08-17
Hello, everyone.

It's been some time since I tried to get the sound working on this portable and I've decided to try again. Alsa doesn't recognize my sound card (afaik). The sound card is realtek alc262. Laptop's make and model: Toshiba Tecra a8 PTA83E. 

Here's the output of alsa information script:
[http://www.alsa-project.org/db/?f=517c26bacded346fb79280a411e393cee4f88c7e](http://www.alsa-project.org/db/?f=517c26bacded346fb79280a411e393cee4f88c7e)

I'm running Ubuntu 11.04 and Windows xp on a seperate partition and sound doesn't work on both. :(

Hope you can help.

---

### Post by originalchoice on 2011-08-17
Okay,this solution fixed it for me in Ubuntu and Windows alike:

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/115966](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/115966)

---

