---
title: "Wine refuses to work!"
date: 2008-07-16
forum: General Help
---

### Post by Markissocoollike on 2008-07-16
ok here's the issue: I Had wine and winedoors working perfectly before that is until I was trying to get Dreaweaver MX to work, my wine then refused to open any of the windows applications, when I tried to open an application nothing happened the only thing which seems to work is notepad under wine>program>accessories

I then tried to reboot the whole system and guess what? It's still doing the same thing as if ubuntu had not been unistalled which it had and yes I have tried using older versions and used winedoors nothing seems to work and I also found something stange about the directory i was using whenever I put /host it says its a directory but when I put /host/Program Files it says it doesn't exist I presumed it was the space in Program Files but it just sent me the same message once I renamed it... so whats wrong!?

---

### Post by jimv on 2008-07-16
Sounds like your Wine install got hosed.  You can reset it (you'll lose your windows apps) by deleting the .wine folder in your home directory.

---

### Post by Markissocoollike on 2008-07-16
yeh heres the thing: I checked that directory and I don't got it I got:
bin,
Drsktop,
Documents,
Examples,
Music,
Pictures,
Public,
Templates,
Videos
but no .Wine I'm afraid

---

### Post by Viper666 on 2008-07-16
yeah... uninstall whatever version you have by 
```
sudo apt-get remove wine --purge
```

and manually delete the .wine folder

reinstall the latest wine version and see if that solved it

---

### Post by Viper666 on 2008-07-16
> **Markissocoollike said:**
> yeh heres the thing: I checked that directory and I don't got it I got:
bin,
Drsktop,
Documents,
Examples,
Music,
Pictures,
Public,
Templates,
Videos
but no .Wine I'm afraid


press CTRL + H to show the hidden folders... you will prolly see the .Wine folder now :)

PS: to "link" to a folder containing spaces you must write it like this:

example: /host/Program\ Files/... (put an "\" before any space

---

### Post by Markissocoollike on 2008-07-16
> **Viper666 said:**
> press CTRL + H to show the hidden folders... you will prolly see the .Wine folder now :)

omg I feel as stupid as that dell support caller lol!

---

### Post by Viper666 on 2008-07-16
there are no stupid questions... so don't worry. We are all here to help

---

### Post by Markissocoollike on 2008-07-16
O-M-G! I can't believe wine is still not working  might have to change my os completely lol!

---

### Post by Markissocoollike on 2008-07-16
I've added a comment to Wine-Doors 0.1.2 - Pretty much broken :( thread on the Wine-Doors site hopefully they will see it and fix the problem with the new patch I'm very annoyed right now >:(

---

### Post by Markissocoollike on 2008-07-16
ok I've got an idea I'll try installing any windows apps I want with wine and see if that works, it seems to run notepad ok so I see no reason why this idea won't work!

---

### Post by Viper666 on 2008-07-16
hmmm... what version of wine are you using (also specify if u installed it through synaptic or downloaded it from WineHQ) and what Ubuntu version are you running?

> "wine is still not working" what does it show in the debug console? What's the error?

---

### Post by quantum-positron on 2008-07-16
you might want to look into aptana studios if you are not empirically stuck with dreamweaver. I have as yet to find any functionality differences

---

### Post by Markissocoollike on 2008-07-16
> **Viper666 said:**
> hmmm... what version of wine are you using (also specify if u installed it through synaptic or downloaded it from WineHQ) and what Ubuntu version are you running?

 what does it show in the debug console? What's the error?

latest and it says it can't find directory

---

### Post by Markissocoollike on 2008-07-16
> **quantum-positron said:**
> you might want to look into aptana studios if you are not empirically stuck with dreamweaver. I have as yet to find any functionality differences
I think i'd rather just run windows when I run into that problem

---

### Post by Markissocoollike on 2008-07-16
I try to run warcraft 3 and I get a load of green lines funny...

---

### Post by Viper666 on 2008-07-16
> **Markissocoollike said:**
> latest and it says it can't find directory

umm what's the actual command line your using to start up the programs?

---

### Post by Markissocoollike on 2008-07-16
> **Viper666 said:**
> umm what's the actual command line your using to start up the programs?

I don't use one I use Applications>wine>programs>warcraft 3 > warcraft 3 however it still aint working

---

### Post by Viper666 on 2008-07-16
well i need a debug output too actually understand what the error is..

open a terminal window

type... ```
sudo cd /(path to application folder)
```

example: sudo cd /host/program\ files/Warcraft3

and then type... wine (application name.exe)

example: wine warcraft3.exe

(if there is an error it will be shown in the terminal window... copy that over here and i can understand better where the problem is)

---

### Post by Markissocoollike on 2008-07-16
bash: cd: /host/program files/Warcraft3: No such file or directory

I'm getting so fed up of this stupid message coming up every two seconds I might change for a better os I heard of this puppy linux thing and it seems a better option because this stupid os just refuses to work wine properly maybe its a sign that im better off with puppy linux bye bye ubuntu

---

### Post by jimv on 2008-07-17
Why are you putting /host?  Obviously it doesn't exist...and I have no idea why you think that it would.  Wine stores everything in /home/YOU/.wine/drive_c...unless you specifically set it to put it elsewhere.

Please post the output of these commands:

ls /
ls /host
ls ~/.wine/drive_c

---

