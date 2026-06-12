---
title: "[SOLVED] Default Sound Card?"
date: 2008-10-23
forum: General Help
---

### Post by small_sammy on 2008-10-23
Hi there,

I have Xubuntu 8.04 and ASUS P5VD2 motherboard.
The mobo has an onboard sound card but I have also installed in the system a Terratec DMX6 fire soundcard.
Both of them are recognized by the system but it seems the default one is the onboard...sound comes only from there...
I am trying to figure out a way to change the default card to Terratec but I have no results...I thought about disabling the onboard card from BIOS but strangely there is no option for that there...

Any ideas?

Thanx!

---

### Post by kpkeerthi on 2008-10-23
1. Find the list of cards available and detected:
```
asoundconf list
```
This would print something like:
AAA
BBB

2. Now set the default card:
```
asoundconf set-default-card <card-name-from-step-1>
```
Eg: asoundconf set-default-card BBB

To undo (should something break):
```
asoundconf reset-default-card
```

---

### Post by small_sammy on 2008-10-23
That did the trick!!

Many thanks!

---

