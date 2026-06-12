---
title: "Ubuntu 14.04 LTS not using 1280x800 display on Sony Vaio SZ360P w/Nvidia graphics"
date: 2016-01-30
forum: Hardware
---

### Post by Stephen_Cobb on 2016-01-30
I am generally delighted by how well Ubuntu 14.04 LTS runs on my older Sony Vaio SZ360P laptop, except it is not using all of the 1280x800 display. It is stuck in 4:3 aspect ratio which leaves black pillars either side of the OS screen. I use this machine for a variety of experiments and could live with this issue if I had to, BUT, I'd love to be able to use the whole display real estate. These VGN series machines have Nvidia graphics (and are quite hot, despite age).

Anyone solved this issue in 14.04?

Many thanks in advance for pointers, and for being such a cool OS.

Stephen

---

### Post by weatherman2 on 2016-01-30
Did you try adding the Additional Driver for the Nvidia graphics card?  If not, you should do that - the proprietary Nvidia driver will probably work better (and may have more resolutions) than the open source driver you get by default.  Search the dash for "Additional drivers" and then just follow the prompts.

---

### Post by Stephen_Cobb on 2016-01-31
Doh! <slaps forehead> I should have thought of that: "try adding the Additional Driver for the Nvidia graphics card...Search the dash for "Additional drivers" and then just  follow the prompts."

I guess I spent too much time with early Linux when the answers were never that simple. I am now trying the Nvidia drivers and pretty sure that will fix it, so that's a ot for such a quick and helpful reply.

(The first Nvidia driver seems to have made the system slightly unstable, but no worries, I will try the others.)

Cheers...Stephen

---

