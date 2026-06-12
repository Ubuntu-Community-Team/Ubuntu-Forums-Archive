---
title: "Trying to use different hard drives"
date: 2008-08-23
forum: General Help
---

### Post by jakem91 on 2008-08-23
hey everybody, i just recently installed ubuntu on one of my older computers and it works great. just recently though i got a hp pavillion xt936 for free with a xp harddrive. this computer has the option of having 2 harddrives in it so i put the hd with ubuntu on it and put it as the master and the one with xp as the slave. but when i go to turn it on it reads "please insert system disk and press enter". Im not really sure what to do. if the is helps i put in 512mb of ram in it but that shouldnt make a difference and if i unplug the slave it works great.

---

### Post by Elfy on 2008-08-23
Have you set the jumper correctly on the drives - check that the slave is set as slave. You them as master and slave in the BIOS.

---

### Post by jakem91 on 2008-08-23
this comp doenst have a bios but it does have a setup and a POST or watever that is

---

### Post by Elfy on 2008-08-23
Yes - setup will get you into the bios, but you need to check the physical jumpers on the back of the hard drives to make sure they are set up correctly. BIOS should show the current state - but if it doesn't you'll have to check.

---

### Post by jakem91 on 2008-08-30
i figured it out i didnt have the jumpers right but now my 20.5gb harddrive is reading as a 9.1 gb harddrive any suggestions.

---

### Post by Elfy on 2008-08-30
Can you open a terminal and run 
```
df -h
``` to start with please

---

