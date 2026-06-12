---
title: "Can't disable twinhead setting"
date: 2008-08-15
forum: General Help
---

### Post by Roger D on 2008-08-15
Hi

I'm trying to switch from a twinhead dual monitor setting, to a single monitor setting. I was pretty sure I knew how to do this, but when I come to do it in anger, I just can't get it to work.

Here's what's happening:

System>Administration>NVIDIS X Server Settings

I select X Server Display Configuration

Click on my Samsung monitor image, the monitor I want to disable.

Click on the Configuration box

Select the Disabled option, click on OK

Click on Save to X Configuration File

The Save X Configuration window opens, I can see /etc/X11/xorg.conf, and the merge with existing file box is ticked.

I click on Save, and get the message:

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'

I click on OK, the only option, and Quit

And nothing happens.

Any ideas?

Roger D

---

### Post by Elfy on 2008-08-15
Open it from the terminal

```
gksudo nvidia-settings
```

It doesn't appear to open as root from the menu - more or less useless if you ask me ;)

If that doesn't work edit xorg by hand.

---

### Post by iaculallad on 2008-08-15
Or:

```
gksudo nvidia-xconfig
```

---

### Post by Roger D on 2008-08-15
Many thanks. Works a treat.

Roger D

---

