---
title: "My sound plays in both Stereos and headphone"
date: 2010-06-05
forum: Hardware
---

### Post by deathvoice on 2010-06-05
hello, i have a problem that i can't get fixed..
whenever i play a sound or a video in  my ubuntu it plays in both my headphone and stereos, how can i play the sound only through the headphone

---

### Post by lidex on 2010-06-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by dileepm on 2010-06-06
Go to audio control and mute the option PCM to turn off Headphones. This works for me.:KS

---

