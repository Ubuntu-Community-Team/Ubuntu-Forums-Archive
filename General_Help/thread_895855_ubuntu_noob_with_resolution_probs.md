---
title: "ubuntu noob with resolution probs"
date: 2008-08-20
forum: General Help
---

### Post by OmegaMef on 2008-08-20
Just installed Ubuntu hardy heron so I'm a complete noob.
I have my TV connected to my computer as well as a monitor but i only use the TV to watch videos full screen.

my monitor will go to 1280x0124 but Ubuntu will only go to 1280x768, i think this might be because it's giving me dual screens and is making them both the same size, but i only want to use my monitor, I'd like to leave my TV plugged in but disable it through software but don't know how to do this yet.

(also i want to know how to install flash but i want the resolution sorted out first)

---

### Post by WRDN on 2008-08-20
> **OmegaMef said:**
> Just installed Ubuntu hardy heron so I'm a complete noob.
I have my TV connected to my computer as well as a monitor but i only use the TV to watch videos full screen.

my monitor will go to 1280x0124 but Ubuntu will only go to 1280x768, i think this might be because it's giving me dual screens and is making them both the same size, but i only want to use my monitor, I'd like to leave my TV plugged in but disable it through software but don't know how to do this yet.

(also i want to know how to install flash but i want the resolution sorted out first)

To disable the second monitor (if not done so already), open the Terminal and type:

```
sudo displayconfig-gtk
```

This will open the Screen and Graphics Preferences program. Now, select "Screen 2" and then click the Disable radio button. You can also set the resolution you want for the monitor here.

---

### Post by OmegaMef on 2008-08-20
thanks for your help, turns out that the second monitor is disabled. It still doesn't give me any resolutions higher than 1280x768.
I pressed the "Test" button and this did display full screen but i couldn't read the message that was displayed as it was too burly.

---

