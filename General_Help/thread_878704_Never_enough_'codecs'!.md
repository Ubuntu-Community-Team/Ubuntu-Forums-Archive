---
title: "Never enough 'codecs'!"
date: 2008-08-03
forum: General Help
---

### Post by Redptc on 2008-08-03
While I thought everything was going really well I discovered today that I am short of a "Real Audio Decoder"!

I tried to listen to some music on a TV station web but I was rejected. I have Real Player running so that I get Real Player videos etc. Flash works like gangbusters but now it looks like I am not complete.

What is "Real Audio Decoder" and where do I get this 'can't live without' feature? Should I just download all the 'codecs' listed in the Ubuntu repository and hope?

Can anyone provide a bit of guidance, please?

---

### Post by billgoldberg on 2008-08-03
Use this command to install all codecs

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by Redptc on 2008-08-03
> **billgoldberg said:**
> Use this command to install all codecs

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

WOW, did I really need that?? Thanks, I guess you answered my question. 

Erm, When does the 'download' finish? I got to the 'Sun' terms, is that the END?

---

### Post by sisco311 on 2008-08-03
i think mplayerplug-in can play real audio files:
```
sudo aptitude install mozilla-mplayer
```

---

### Post by Redptc on 2008-08-03
> **Redptc said:**
> WOW, did I really need that?? Thanks, I guess you answered my question. 

Erm, When does the 'download' finish? I got to the 'Sun' terms, is that the END?

If you are considering using this 'to install all codecs', it is a 'handful' so be warned!

---

### Post by Redptc on 2008-08-03
Now I have ALL the codecs this thing still doesn't work!

---

### Post by dje on 2008-08-03
try the guide [here]("http://www.ubuntu1501.com/2008/04/easy-media-codec-installation-for-hardy.html")

dje

---

