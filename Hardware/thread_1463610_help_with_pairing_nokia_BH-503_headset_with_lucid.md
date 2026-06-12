---
title: "help with pairing nokia BH-503 headset with lucid"
date: 2010-04-27
forum: Hardware
---

### Post by squiddy on 2010-04-27
i've used sudo hcitool scan and no result of detected device. i'm desperate. help please.

---

### Post by squiddy on 2010-04-27
bump...:popcorn:

---

### Post by matiasg on 2011-01-21
This question is pretty old now, but this may help some lost soul (as I was, one hour ago).
Install blueman
```
sudo aptitude install blueman
```and launch it (either by blueman-manager, or from the System -> Preferences menu, in "Bluetooth manager").
Don't forget to select custom pin code, and enter 0000 in order to pair the headsets. And also, use it as "audio sink".
Finally, open sound preferences, and select the headsets in the "output" tab.

---

### Post by ubu_arpit on 2011-07-18
**Thnx alot for the info** :)

---

### Post by kunaldragonball on 2011-08-02
HI,

I also have brought Nokia bh-503 bluetooth headsets.. 
I am able to see device in bluetooth scanning using blueman or hcitool. however am not able to connect it or even pair it even if I choose custom pin. Please Help me.
I am getting desperate for help.It;s been weeks am trying to use it. I tried on windows machine and it works like charm..I don;t want to switch to windows again.

---

### Post by stjohnmedrano on 2012-01-23
> **kunaldragonball said:**
> HI,

I also have brought Nokia bh-503 bluetooth headsets.. 
I am able to see device in bluetooth scanning using blueman or hcitool. however am not able to connect it or even pair it even if I choose custom pin. Please Help me.
I am getting desperate for help.It;s been weeks am trying to use it. I tried on windows machine and it works like charm..I don;t want to switch to windows again.

Same problem here. [http://askubuntu.com/questions/96539/ubuntu-11-10-dont-recognize-bluetooth-phone](http://askubuntu.com/questions/96539/ubuntu-11-10-dont-recognize-bluetooth-phone).

just need to turn on until the light turns to green and blue.

---

