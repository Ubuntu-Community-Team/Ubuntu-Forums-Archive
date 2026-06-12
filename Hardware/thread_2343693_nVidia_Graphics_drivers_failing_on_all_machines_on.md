---
title: "nVidia Graphics drivers failing on all machines one after another"
date: 2016-11-18
forum: Hardware
---

### Post by ipk on 2016-11-18
Hello everybody,

we have at work some 10 Dell Precision workstations (T3500, T5500, T7500) with different kinds of nVidia Quadro cards: FX3500, 3800 and 4500 running Ubuntu 14 or 16. Many of them are running different versions of the nVidia drivers, depending on the precise model of Graphics card. 

At home I have two additional PCs running Ubuntu 12 and 14, also with nvidia cards.

 In the last weeks now one after another of these began to freeze on me and could only be rescued by a complete uninstall of xorg and nvidia followed by a re-install of xorg, but NOT nvidia, and they are now running without the nvidia drivers. All of theses have been running flawlessly, some for many years, and I am now really close to completely abandonning Ubuntu. The suspicious issue is, that it is not only one particular Ubuntu version (having running here 12, 14, and 16) nor nvidia driver (using 304, 341 and others on the different machines).

I have tried to search the forums by putting "nvidia" into the search box on top, but got no hits (even though I could find posts with "nvidia" in the subject title through browsing), so please excuse if I am bringing up a question that has long since been answered and kindly point out the links to me.

Any ideas???

Greetings

Ingo

---

### Post by ajgreeny on 2016-11-18
I have never had an nvidia card to deal with but first question is, "how did you install the nvidia drivers?"

If you used the Additional Drivers utility all ought to be good, but if in any other way try what is shown at [http://askubuntu.com/questions/760997/how-to-recover-from-a-nvidia-fail-on-ubuntu-16-04](http://askubuntu.com/questions/760997/how-to-recover-from-a-nvidia-fail-on-ubuntu-16-04)

I do not know if it will help you but it must be worth trying, I think.

---

### Post by ipk on 2016-11-19
Some of the machines ran fine with the drivers from the "additional drivers" utility, and some did not and i had to work my way through the nvidia drivers from their webpage until i found one that worked. As I said, they have been running fine, some of them for as long as five years, and now the started failing one after another ...
And I guess, the suggestion from the posts is exactly what I have done now: uninstall nvidia and run on nouveau. Unfortunately performance of nouveau is really poor for the 3-d applications we are running. Multiple screens, stereo and so on ...

---

