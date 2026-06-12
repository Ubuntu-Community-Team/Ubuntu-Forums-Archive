---
title: "No sound in ubuntu 9.10"
date: 2010-05-15
forum: Hardware
---

### Post by gaurav sontakke on 2010-05-15
Hi All
  I am newbie in Ubuntu I have just now installed ubuntu 9.10 on my lenovo laptop.
                                         After some days of installation I was able to here sound **but I dont know what happened but sounds stops automatically from ubuntu ..**I cant here any sound from laptop ....
please help me out
                                  whats the problem ??
Thanking You in advance

---

### Post by byStanderone on 2010-05-15
...there must have been an update done by the system and an old file needed by your audio system was replaced by a new one which is not at all compatible with your existing audio setup, you can try booting in restore mode, to findout if it corrects the problem. or perhaps go to synaptic manager to see if there is/are files uninstalled that is needed by your audio....you can reinstall it/them.

---

### Post by gaurav sontakke on 2010-05-15
how can i find that files?? which need to be get installed ... and Yes I have updated my system ...
   I have tried recover files by rebooting but it gives the same result no sound yet

---

### Post by blchinezu on 2010-05-15
i had a similar problem with karmic with my asus x55sv
this solved my problem at the time:
> sudo killall pulseaudio
sudo alsa force-reloadthe only problem is that i had to run it each time i booted so i made it as script and runned it at startup. the script looked like this
> #!/bin/bash
echo "YOUR_PASSWORD" | sudo killall pulseaudio
echo "YOUR_PASSWORD" | sudo  alsa force-reloadwhere YOUR_PASSWORD, obviously is to be replaced by the user password

you can try running the commands in terminal and if it works set it as script in startup until you find a better solution

edit: and another thing.. after reloading alsa the volume always was at 0% and so i had to raise it to a decent value to actually hear something.

---

### Post by gaurav sontakke on 2010-05-15
> **blchinezu said:**
> i had a similar problem with karmic with my asus x55sv
this solved my problem at the time:
the only problem is that i had to run it each time i booted so i made it as script and runned it at startup. the script looked like this
where YOUR_PASSWORD, obviously is to be replaced by the user password

you can try running the commands in terminal and if it works set it as script in startup until you find a better solution

edit: and another thing.. after reloading alsa the volume always was at 0% and so i had to raise it to a decent value to actually hear something.
Thanks sir 
it works for me ..
but do you know any descent reason for this ???:P
why this is happening ???
thank you

---

### Post by blchinezu on 2010-05-15
I have no ideea.. In karmic the sound worked until the first update after which I had no sound.. The hardware simply wasn't recognized.. After reloading alsa it worked.. I have no ideea why that happened but it seems to be solved with Lucid. I supose there was some problem with alsa. Anyway I never searched for another solution as this was enough for me.

---

