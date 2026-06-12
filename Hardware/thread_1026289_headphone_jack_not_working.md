---
title: "headphone jack not working"
date: 2008-12-31
forum: Hardware
---

### Post by Dumbestcrayon on 2008-12-31
I actually finally fixed this issue.

I was having an issue with my headphone jack not working on my Toshiba A135-S4527 laptop. Ubuntu didn't even pretend to know it was there. When I plugged in the headphones it did not play through the headphones nor did it shut off the speakers. This is how I ended up fixing it.

```
sudo gedit /etc/modprobe.d/alsa-base
```

Then I added this line to the bottom..
```
options snd-hda-intel model=lenovo
```


I wanted to post this because..

1. People all over the internet and several forums are having this issue.
2. If I ever have to reinstall Ubuntu for any reason I will have my fix posted where I can find it :)

---

### Post by Messyhair42 on 2008-12-31
i'm having the same problem. i'm just wondering if i edit the file should i use the same line of code i.e. is the 'lenovo' specific to your hardware or is it more general than that?

---

### Post by Dumbestcrayon on 2008-12-31
Do you have the same laptop as me? I believe its specific to my hardware. I actually found that somewhere on google. If you have a laptop post the model of it here please.


Try this one..

```
options snd-hda-intel model=auto
```

---

### Post by Messyhair42 on 2008-12-31
actually it's a self-built desktop i'm having the problem with. i have an internal sound blaster card and an intel DG43NB motherboard.

---

