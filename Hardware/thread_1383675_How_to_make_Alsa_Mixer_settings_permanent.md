---
title: "How to make Alsa Mixer settings permanent"
date: 2010-01-17
forum: Hardware
---

### Post by MontoyaF1 on 2010-01-17
This was already asked in the "Beginner Talk" forum and I wasn't getting any answers.

I just upgraded to Ubuntu 9.10 and the External Amplifier button is checked. I tried the below but it still won't save my changes, so every time I reboot I have to go into Alsamixer to uncheck that stupid box. What gives?  :(

> 
- Get the settings exactly the way you want them.
 - *sudo alsactl store* into the terminal.
 - Edit the /etc/rc.local file as root and then add in the line *alsactl restore* before exit 0
 - reboot


---

### Post by sisco311 on 2010-01-17
try to delay the command:
```
sleep 10 &&  alsactl restore
```

---

### Post by ajgreeny on 2010-01-17
I always thought it was ```
sleep 10; alsactl restore
```Surely if you use the && sleep will not know which command to make sleep.  Perhaps I just don't understand the sleep command, however.

EDIT.
I should have tried this way, which certainly does work.  I never knew that way of using sleep!

---

### Post by MontoyaF1 on 2010-02-05
> 
Code:
sleep 10 && alsactl restore
__________________
 
Okay, I followed the above and it didn't work:
1. I logged in 
2. Changed my alsamixer settings to the way I wanted them (checkmark for External Amplifier radio button)
3. /etc/rc.local already has "*alsactl restore"* before the "exit 0" from a previous attempt, so I didn't touch the file this time
4. I typed "sudo sleep 10 && alsactl restore" and entered my password
5. I closed the terminal window
6. I then rebooted
 
What am I doing wrong now?  :confused:

---

### Post by MontoyaF1 on 2010-02-17
Anyone???

---

### Post by Cold Man 1 on 2010-08-04
Finnaly figured it out after sum searching and i dink dis shud work 4 every1....
on luicd ::
open terminal, alsa and set your settings,exit
open terminal again and type in 
"sudo alsactl store 0"

go to system,preferences, startup applications and add a startup program with this code ....
 "sudo alsactl restore"
reboot and done! 
no need to thank me but plz donate for my open source hack of ubuntu coming out soon!

---

### Post by amenfex on 2010-08-13
I'm having the same issue, only karmic.

Unfortunately, I haven't been able to get lucid to install on my laptop.

Never the less, I have followed these same steps with no results.

Any suggestions?

---

### Post by shadowpt on 2010-10-19
sisco311 command worked like a charm to me! 

amenfex, have you managed to solve your issue?

---

