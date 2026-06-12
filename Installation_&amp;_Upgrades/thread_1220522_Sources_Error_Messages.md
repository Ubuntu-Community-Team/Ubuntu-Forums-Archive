---
title: "Sources Error Messages"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by slimrider94 on 2009-07-22
I am a brand new Ubuntu user and I finished installing the operating system today. Lately, I have been getting numerous error messages when I try to launch the "Update Manager", "Add/Remove...", and "Synaptic Package Manager." I have taken screenshots to further help you guys understand my problem.

(gave links because the images are big)
**Screenshot 1**
[http://img4.raidpic.com/48Screenshot.png](http://img4.raidpic.com/48Screenshot.png)

**Screenshot 2**
[http://img7.raidpic.com/87Screenshot_1.png](http://img7.raidpic.com/87Screenshot_1.png)

**Screenshot 3**
[http://img7.raidpic.com/17Screenshot_2.png](http://img7.raidpic.com/17Screenshot_2.png)

I tried to do the sudo updates in the Terminal but it gives an invalid install message. Any help would be appreciated. I'm go to try re-installing Ubuntu.

---

### Post by shifty21 on 2009-07-23
Diddo for me. I just installed Ubuntu Netbook Remix. When initally completed the install, there were numerous updates for me. The Synaptic Package Manager handled them with no problems. Now when I go in to it to refresh, there are all sorts of errors.

---

### Post by eternalsword on 2009-07-23
Would help if you gave the contents of you /etc/apt/sources.list file.  Just paste the contents in here, select it and click the # button.

---

### Post by slimrider94 on 2009-07-23
> **eternalsword said:**
> Would help if you gave the contents of you /etc/apt/sources.list file.  Just paste the contents in here, select it and click the # button.

Sorry for being a little noob here but how exactly do I get the sources list file for you?

---

### Post by drs305 on 2009-07-23
Open a terminal (Applications, Accessories, Terminal) and type in:
```

cat /etc/apt/sources.list

```

The easiest way to copy from a terminal window is just to highlight it and then paste it by clicking your middle mouse button. Otherwise, to copy contents inside a terminal window: CTRL-SHIFT-C

---

### Post by slimrider94 on 2009-07-23
> **drs305 said:**
> Open a terminal (Applications, Accessories, Terminal) and type in:
```

cat /etc/apt/sources.list

```The easiest way to copy from a terminal window is just to highlight it and then paste it by clicking your middle mouse button. Otherwise, to copy contents inside a terminal window: CTRL-SHIFT-C

Thanks man, will do this, first I gotta take care of some things.

---

### Post by shifty21 on 2009-07-24
I tried updating again before I posted and poof! it works now. Perhaps the hosting server had a hiccup when I was trying?

---

