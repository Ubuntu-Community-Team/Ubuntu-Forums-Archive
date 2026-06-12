---
title: "installing *.bin files"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by it_suppport on 2008-12-05
Dear All,

How to install any package which is in *.bin format.
I want to install openCRX on ubuntu 8.0.4 server along with oracle jvm
both are in *.bin format & not getting installed with dpkg, alien, symaptic or aptitude.

---

### Post by ChrisBookwood on 2008-12-05
Now, don't shoot me if doesn't work, but can't you just go to a terminal and type:```
./path/to/the/bin/file
```which will run the bin file.

Does it work?

---

### Post by it_suppport on 2008-12-05
no its not working....

---

### Post by ChrisBookwood on 2008-12-05
Are you sure? Can you poste you conversation with the terminal?

---

### Post by Perfect Storm on 2008-12-05
What apps are you trying to install?

---

### Post by ChrisBookwood on 2008-12-05
> **Artificial Intelligence said:**
> What apps are you trying to install?

openCRX and oracle jvm

---

### Post by Perfect Storm on 2008-12-05
Do a;
```
cd <path>
chmod +x <file>
sudo sh <file>
```

---

### Post by ChrisBookwood on 2008-12-05
> **Artificial Intelligence said:**
> Do a;
```
cd <path>
chmod +x <file>
sudo sh <file>
```

Just for reference ... if a file has been done executable (chmod +x), it's not neccesary to do "sh <file>" - you can just 'run it' (./<file>, or whatever way you like)

---

### Post by Perfect Storm on 2008-12-05
old habit dies hard.

---

### Post by TitanX13 on 2008-12-10
i was having a same if not similar problem with google earth for linux. i got to work thanks to your help
i just

switched it to a excutivable then.. 

cd /home/???????/Desktop 
 Chmod +x googleearthlinux.bin
 then...
 Sudo ./googleearthlinux.bin 

and now it works

thank you

---

