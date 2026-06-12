---
title: "sound issues"
date: 2012-07-01
forum: Hardware
---

### Post by Shadow819 on 2012-07-01
hello. new person here. i was wondering if anyone could help me out with a sound problem i am having with my desktop. its the first time iv encountered it and im honestly not even sure were to get started much. iv checked and made sure everything is not muted and cycled through every option i could in the sound setting but had no luck at all. even tried some of the things people posted in the past but again. no luck. if anyone at all could help me i would greatly appreciate it, thanks.
running natty 11.04 if it helps

---

### Post by IWantFroyo on 2012-07-01
Run this in Terminal:

```
alsamixer
```

If either the Master channel or speakers are muted, hit m over them to unmute them (there should be "00" there).

---

### Post by Shadow819 on 2012-07-01
> **IWantFroyo said:**
> Run this in Terminal:

```
alsamixer
```If either the Master channel or speakers are muted, hit m over them to unmute them (there should be "00" there).
i tried and they werent muted.still no sound. do you have any other ideas please? :)

---

### Post by Shadow819 on 2012-07-07
can someone please help me with this "been at it over 6 hours". iv tried upgrading to the latest distro. going through multiple sites on editing the alsa config files and still had no luck. im about to go get a separate sound card in hope it will work even but i dont want to spend the money on it just yet =/ . my current one is a realtek alc850. has anyone else had any luck with this card?

---

### Post by msammels on 2012-07-07
Shadow,

Going on the above code, please try this:

```
**sudo** alsamixer
```

As it does require root to run.

---

### Post by Shadow819 on 2012-07-07
> **msammels said:**
> Shadow,

Going on the above code, please try this:

```
**sudo** alsamixer
```As it does require root to run.
everything is unmuted and turned all the way up and there is still no sound.

---

### Post by msammels on 2012-07-07
OK - in Ubuntu, click the sound icon on the top panel, go to settings. Make sure the correct output device is selected.

---

### Post by Shadow819 on 2012-07-07
its selected "analog output / amplifier" "built in audio". i ran through all the settings and tested them just to be sure as well and didnt get anything. 
just as a side note i tested my speakers with my laptop and they do for sure work. as well as plugging them into the multiple outputs in back "sub/front/rear" and none of them work either.

---

