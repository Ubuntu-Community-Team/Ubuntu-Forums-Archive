---
title: "New Monitor Noob q's"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by Burgresso on 2006-07-24
I'm thinking about updating my monitor, a move that would boost my max resolution. I primarily use my Ubuntu for programing and surfing - no need for really for 3d acceleration and stuff, even though my MB has graphics card(s).

Anyhow, should I be able just to plug an play? And if not, is there anyhing I need to be aware of?

gracias

burgresso

---

### Post by ahaslam on 2006-07-24
Hi,

I've heard that the 'vesa' graphics driver only supports up to 1024x768. If you're using this you'll want to install the required hardware specific drivers. I may be wrong about the vesa drivers and I'm sure that someone will correct me if I am. If  you've got the correct drivers installed it should just be a case of adding the higher resolutions to your xorg.conf.

I hope that helps.

Tony.

---

### Post by Burgresso on 2006-07-24
Thanks.

When Ubuntu installs, it detects the monitor and hardware, and sets up a/the drivers, right?

Right now my on-board VGA input on my xorg.conf does have the "vesa" card - I tried changing it to "nv" but it forced my resolution to 630 x something.

Anyhow, should I be able to install different video cards if I get a new monitor and the resolution does not increase - or is it more hardware dependent? Should/would/could I need a video card?

gracias,

burgresso

---

### Post by ahaslam on 2006-07-24
If your graphics card is not listed or is not 100% the same as what is, Ubuntu will install the generic 'vesa' drivers.
Let us know what graphics card you're using and we may be able to help with the installation of the correct drivers. This should dramatically increase  performance & enable you to use higher resolutions. 

Tony.

PS. Don't blow your money on a new card yet, have faith in the community. ;)

---

### Post by Burgresso on 2006-07-24
Thanks Tony; lets see if we can get this...:) 

My on-board graphics card is the NVIDIA GeForce 6100 + NF410.

Any thoughts?

gracias

burgresso

EDIT:

For now, I'm just going to jump and try this....[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
Wish me luck!

---

### Post by Burgresso on 2006-07-24
Oh yea! And it works like a charm - the curser blinks a tiny tiny bit, but that may be normal. Your right - my computer flies now! thanks!

8)

---

