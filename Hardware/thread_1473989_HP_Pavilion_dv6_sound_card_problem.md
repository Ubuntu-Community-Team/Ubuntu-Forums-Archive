---
title: "HP Pavilion dv6 sound card problem"
date: 2010-05-05
forum: Hardware
---

### Post by ermank on 2010-05-05
Hi,

I have installed ubuntu 10.4 today and i have some problems with the sound. it just wont work.

I know there is other threads about this topic but they just dont seem to work for me.
when i run:
sudo aplay -l
it gives me this output
aplay: device_list:223: no soundcards found...

can somebody help:)

---

### Post by lidex on 2010-05-05
Try this. Using a Terminal="Applications->Accessories->Terminal"
enter these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall ubuntu-desktop
```
One line at a time please. Enter your user password when prompted.

---

### Post by ermank on 2010-05-06
Thanks lidex for your reply!
but it didnt work:(

---

### Post by lidex on 2010-05-06
OK. Now this. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by SebSmith on 2011-02-27
> **lidex said:**
> OK. Now this. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.


sebastian@sebastian-hp:~$ uname -a
Linux sebastian-hp 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
sebastian@sebastian-hp:~$ aplay -l
aplay: device_list:235: no soundcards found...
sebastian@sebastian-hp:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
sebastian@sebastian-hp:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory


envy 14

---

### Post by lidex on 2011-03-01
> **SebSmith said:**
> sebastian@sebastian-hp:~$ uname -a
Linux sebastian-hp 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
sebastian@sebastian-hp:~$ aplay -l
aplay: device_list:235: no soundcards found...
sebastian@sebastian-hp:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
sebastian@sebastian-hp:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
envy 14

Your alsa install is borked. Try re-installing.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

