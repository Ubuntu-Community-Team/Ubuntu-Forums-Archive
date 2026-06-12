---
title: "how do you overclock nvidia cards on ubuntu?"
date: 2009-02-20
forum: Hardware
---

### Post by NeferalCrossfireX on 2009-02-20
i know it can be done, but any info would really help:grin:

---

### Post by sdennie on 2009-02-20
In /etc/X11/xorg.conf, search for 'Driver "nvidia"' and add the following line to that section:

```

Option "Coolbits" "1"

```

The next time you restart X, nvidia-settings will have the ability to over/underclock your video card.

---

### Post by jerrrys on 2009-02-20
over/underclock your FSB i understand, but your video card, whats up with that??

---

### Post by NeferalCrossfireX on 2009-02-20
> **sdennie said:**
> In /etc/X11/xorg.conf, search for 'Driver "nvidia"' and add the following line to that section:

```

Option "Coolbits" "1"

```

The next time you restart X, nvidia-settings will have the ability to over/underclock your video card.

B-E-A-U-T-I-F-U-L!! worked like a charm, didn't realise it was that simple. cheers!!

---

### Post by wingnux on 2009-05-20
I have a small issue with overclocking my card. After enabling coolbits and overclocking on nvidia-settings I used the "Auto detect" option and it gave me a nice boost on 3D processing but even if I press the "Apply" button those settings aren't kept on the next boot so I have to run the auto detection every single time I login to X. 

Any help?

PS.: I've installed the latest beta drivers manualy, not by using the hardware drivers or synaptic.

---

### Post by tgeer43 on 2009-08-28
wingnux,

As I saw in a HowTo on overclocking nvidia cards, this is more of a feature than an issue. Unless the *only* thing you do with Ubuntu is 3D gaming and other intensive rendering apps then you wouldn't really want to keep it wide open all the time, would you? When you're ready to fire up your favorite FPS *then* it's time to crank it up! Things will run cooler most of the time and probably live longer too.

tgeer

---

