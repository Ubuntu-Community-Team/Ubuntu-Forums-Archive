---
title: "[SOLVED] Basic compiz question"
date: 2008-07-21
forum: General Help
---

### Post by moody_mark on 2008-07-21
Ive installed compiz and selected the "simple" desktop effects. Im running Hardy 8.04 (upgraded from 7.01 with Gnome) and installed KDE.

Ive tried a couple of shortcut keys like ALT+F1 that works, but I cant get any effects. What am I missing? I know its going to be something silly. Also what is the "super" key? Im using a normal UK laptop style keyboard with no number pad.

---

### Post by overdrank on 2008-07-21
> **moody_mark said:**
> Ive installed compiz and selected the "simple" desktop effects. Im running Hardy 8.04 (upgraded from 7.01 with Gnome) and installed KDE.

Ive tried a couple of shortcut keys like ALT+F1 that works, but I cant get any effects. What am I missing? I know its going to be something silly. Also what is the "super" key? Im using a normal UK laptop style keyboard with no number pad.

Hi and you may look at the sticky in this forum
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)
:)

---

### Post by JagDragon on 2008-07-21
The "Super" key is the Windoze key. As for enabling the really cool effects,
```
sudo apt-get install compizconfig-settings-manager
```And then run the thing.

---

### Post by moody_mark on 2008-07-21
when you say "run the thing" do i just simply type "compiz" in a terminal?

---

### Post by JagDragon on 2008-07-21
In a terminal: ```
compizconfig-settings-manager
```

---

### Post by moody_mark on 2008-07-21
> **overdrank said:**
> Hi and you may look at the sticky in this forum
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)
:)

Thanks this thread seems more about install. I got it all install and even my compizconfig-settings-manager is installed

```
$ sudo apt-get install compizconfig-settings-manager
[sudo] password for curtis:
Reading package lists... Done
Building dependency tree
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
```

I dont see to have something running

```
$ ps -ef | grep compiz
curtis    6727  6582  0 13:18 ?        00:00:00 kwrapper ksmserver --windowmanager /usr/bin/compiz
curtis    6729     1  0 13:18 ?        00:00:00 ksmserver [kdeinit] --windowmanager /usr/bin/compiz
curtis    7100  6850  0 13:29 pts/1    00:00:00 grep compiz
```

---

### Post by McNils on 2008-07-21
Try Alt-F2 and type in **compiz --replace**

---

### Post by overdrank on 2008-07-21
> **moody_mark said:**
> Thanks this thread seems more about install. I got it all install and even my compizconfig-settings-manager is installed

```
$ sudo apt-get install compizconfig-settings-manager
[sudo] password for curtis:
Reading package lists... Done
Building dependency tree
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
```

I dont see to have something running

```
$ ps -ef | grep compiz
curtis    6727  6582  0 13:18 ?        00:00:00 kwrapper ksmserver --windowmanager /usr/bin/compiz
curtis    6729     1  0 13:18 ?        00:00:00 ksmserver [kdeinit] --windowmanager /usr/bin/compiz
curtis    7100  6850  0 13:29 pts/1    00:00:00 grep compiz
```

Hi and there is also the tool compiz-check in that thread I linked.

---

### Post by moody_mark on 2008-07-21
In regards to that compiz-check script. I downloaded and ran it on another machine I have (an older one) and the script says all ok. If I run the "compiz --replace" it complains about the card being blacklisted. Does the script not check for the blacklisting, only other parameters?

---

### Post by moody_mark on 2008-07-21
Anyway, heres the compiz check script output of the machine im trying to get compiz running on
```

curtis@Maggie:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   KDE
 Graphics chip:         ATI Technologies Inc Rage 128 Pro Ultra TF
 Driver in use:         ati
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

---

### Post by overdrank on 2008-07-21
> **moody_mark said:**
> Anyway, heres the compiz check script output of the machine im trying to get compiz running on
```

curtis@Maggie:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   KDE
 Graphics chip:         ATI Technologies Inc Rage 128 Pro Ultra TF
 Driver in use:         ati
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

HI and I believe that graphics card ATI Technologies Inc Rage 128 Pro Ultra TF will not support the graphics for compiz. I had a similar one in a laptop and it did not support 3d

---

### Post by moody_mark on 2008-07-21
:(

Dang! Actually I need to get another graphics card for this PC as its a bit jumpy when you watch full screen video, so any recommendations on something reasonably priced that will also support compiz?

---

### Post by overdrank on 2008-07-21
> **moody_mark said:**
> :(

Dang! Actually I need to get another graphics card for this PC as its a bit jumpy when you watch full screen video, so any recommendations on something reasonably priced that will also support compiz?

I would stick with nvidia myself but I do use ATI also. It would really depend on the motherboard. If it will support a 4x graphics card then you should be able to pick one up at a minimal cost.

---

### Post by moody_mark on 2008-07-22
Ok folks, thanks for your advice. I can consider my problem solved now in so much as its the cheapo graphics card that Ive inherited in this PC. Now time to go spend some £ on one that will run compiz

---

