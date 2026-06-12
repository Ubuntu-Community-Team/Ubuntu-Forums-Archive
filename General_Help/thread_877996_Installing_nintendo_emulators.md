---
title: "Installing nintendo emulators?"
date: 2008-08-02
forum: General Help
---

### Post by grikdog on 2008-08-02
Which is the appropriate forum for questions about getting gsnesx or ZSnes to work?  They are available as packages, but... (?)  Thanks.

---

### Post by Diabolis on 2008-08-02
Just ask.

---

### Post by Rainstride on 2008-08-02
zsnes is in the repo and works right after install.

---

### Post by jualin on 2008-08-02
You can install them using Synaptic Package Manager under System, Administration. The package is called znes. In my case the sound didnt work so I had to run it using this code from the terminal > zsnes -ad sdl Hope this helps!

---

### Post by Zeotronic on 2008-08-02
I was going to wait for an actual question, but since everyone else is jumping the gun, I will too.

The current version of ZSNES doesn't support networked play... if that's what your looking for, you'll need to install v1.42, which can be found, at the latest (I think) in Edgy's repositories (maybe Feisty). Last I knew you could access them from somewhere around [here]("http://packages.ubuntu.com/"), but at the time of writing I seem to be having trouble loading the page.

---

### Post by grikdog on 2008-08-02
> **Diabolis said:**
> Just ask.
Thanks :)

Well, when I run gsnesx or zsnes, I can't get it to recognize a simple Logitech Precision usb controller (although some other games know it's there), and neither of them seem to recognize normal keyboard emulation such that Enter is Select (e.g.), and of course sound is off.

Maybe it's just the case that those emulators don't quite work right with Dell Inspiron 1525 notebooks, but I'm hoping for something simple.

---

### Post by jualin on 2008-08-02
> **grikdog said:**
> Thanks :)

Well, when I run gsnesx or zsnes, I can't get it to recognize a simple Logitech Precision usb controller (although some other games know it's there), and neither of them seem to recognize normal keyboard emulation such that Enter is Select (e.g.), and of course sound is off.

Maybe it's just the case that those emulators don't quite work right with Dell Inspiron 1525 notebooks, but I'm hoping for something simple.

For the sound start the emulator via terminal with the following command > zsnes -ad sdl 

---

### Post by grikdog on 2008-08-02
> **jualin said:**
> For the sound start the emulator via terminal with the following command
Thanks.  Sound works, and the static clears up if I bump the scan frequency to max.  Also, discovered that "Keyboard" input is also Logitch Precision USB Controller if I configure "button" instead of "key" (by simply pressing the button requested for each function!)

So Zsnes works.  I'll put off worrying about gsnes9x for the moment.  Thanks everybody.

---

### Post by jualin on 2008-08-02
Glad we helped you, enjoy running those ROMs. I remember the "good times" with Super Nintendo :lolflag:

---

