---
title: "PLEASE HELP headphone issue with update"
date: 2011-04-26
forum: Hardware
---

### Post by dbug1987 on 2011-04-26
Just recently accepted a "critical security updates" prompt to install 300 and some odd updates for ubuntu. I am a linux n00b beyond your wildest nightmares, so please be patient and as dumbed down as you can be. I've been running linux for all of about 2 weeks.

Once I downloaded these updates... my headphone jack went dead. All other audio works. And I know it was the update that did it, because last time this happened, I reinstalled ubuntu and the headphone jack worked again, and as soon as I installed that update again, the jack died again... so I know the update is what is doing this.

HAAALLP!

---

### Post by lidex on 2011-04-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

