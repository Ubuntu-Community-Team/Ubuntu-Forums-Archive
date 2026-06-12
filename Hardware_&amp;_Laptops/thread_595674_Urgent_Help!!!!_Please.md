---
title: "Urgent Help!!!! Please"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by TheSlayerIsBack on 2007-10-29
i need to get my audio driver up, i have the alsa .15 drivers but i dont know what to do with them XD, i have a Nvidia MCP51 HDA, please HELP ME!!!!! i'm tired of looking and nothing works, i have installed ubuntu several times,

---

### Post by TheSlayerIsBack on 2007-10-29
come on someone has to have this sound card >:(

---

### Post by TheSlayerIsBack on 2007-10-29
come guys there more than one person using this thing please ******* help, all the ******* tutorials i've seen dont do **** i'm getting tired of no one help out.
i was using this one [http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install) but when i try to put something on that directory i get a damn error msg saying i dont have permision XD

---

### Post by taurus on 2007-10-29
You don't have permissions because you need to be root to write or create a directory outside your #HOME.  Therefore, try to put sudo in front of a command, e.g.

```
sudo mkdir /usr/src/alsa
sudo cp downloaddir/alsa* /usr/src/alsa
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TheSlayerIsBack on 2007-10-29
> **taurus said:**
> You don't have permissions because you need to be root to write or create a directory outside your #HOME.  Therefore, try to put sudo in front of a command, e.g.

```
sudo mkdir /usr/src/alsa
sudo cp downloaddir/alsa* /usr/src/alsa
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

tried that and only the 1st one works the second one give me this

```
cp: cannot stat `downloaddir/alsa': No such file or directory
```

---

### Post by taurus on 2007-10-29
If you have read the link that you have provided (**[SIZE="2"]2. Getting the sources[/SIZE]**), you know that you need to replace the **downloaddir** with the actual directory where you have downloaded it.

---

### Post by TheSlayerIsBack on 2007-10-29
> **taurus said:**
> If you have read the link that you have provided (**[SIZE="2"]2. Getting the sources[/SIZE]**), you know that you need to replace the **downloaddir** with the actual directory where you have downloaded it.

sry i guess i was to mad to read:P

---

### Post by kvonb on 2007-10-29
Comprehensive sound problems page:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by TheSlayerIsBack on 2007-10-29
> **taurus said:**
> If you have read the link that you have provided (**[SIZE="2"]2. Getting the sources[/SIZE]**), you know that you need to replace the **downloaddir** with the actual directory where you have downloaded it.

ok i get this msg when i use the dir

```
root@mike-laptop:~# cp /usr/src/alsa
cp: missing destination file operand after `/usr/src/alsa'

```

---

