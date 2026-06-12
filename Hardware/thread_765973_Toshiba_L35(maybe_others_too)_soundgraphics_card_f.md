---
title: "Toshiba L35(maybe others too) sound/graphics card fix"
date: 2008-04-24
forum: Hardware
---

### Post by Unreal223linux on 2008-04-24
I have a toshiba l35 laptop and everything pretty much worked.(had a little confusion getting my ati 200m card working but managed to figure it out. Solution here:
[http://ubuntuforums.org/showthread.php?t=765205](http://ubuntuforums.org/showthread.php?t=765205)


The other potential big head ache was my headphones. Luckily I already knew how to fix it from last time(but the process is a little easier now).

Open terminal and paste in this:
```

sudo gedit /etc/modprobe.conf 
```

Then paste this into the notepad that comes up
```
options snd-hda-intel model=6stack-digout
```
Save it and then reboot. 

After the reboot double click the sound icon in the upper right and then enable all of the controls in options. My headphones were linked to the surround one.(may be different for you I guess)

---

