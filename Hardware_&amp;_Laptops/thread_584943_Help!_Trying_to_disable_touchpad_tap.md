---
title: "Help! Trying to disable touchpad tap"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by allspiritseve on 2007-10-21
I have read that I need to edit xorg.conf in order to disable my touchpad tab feature, but when I edit the file and restart X, I get a command line and an error that kinit could not find something. 

This is the line I'm adding:

```
Option “SHMConfig” “on”
```

What can I do so that X will start up properly and I can configure my touchpad?

Thanks,

Cory

---

### Post by Linicks on 2007-10-21
That is correct way - I use:

```
        Option          "SHMConfig"             "true"
```

Now install qsynaptics.  That is a GUI to enable you to set up the way the touchpad works.

Nick

---

### Post by allspiritseve on 2007-10-21
Huh... maybe my [source]("http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/") is wrong...

I will try that and see what happens.

---

### Post by allspiritseve on 2007-10-21
Success!

Thank you for your help.

---

### Post by allspiritseve on 2007-10-22
It appears that every time I restart, the touchpad settings are set back to defaults... how can I make it so the touchpad is disabled permanently?

Thanks,

Cory

---

### Post by Linicks on 2007-10-22
Run qsynaptics and set up your touchpad. This will save the settings in $HOME/.qsynaptics.

Then go:

System>Preferences>Sessions

and create a new 'startup' entry:

Name: Qsynaptics - Configure Touchpad
Command: qsynaptics -r

And save it. Now when you log in, settings are applied correctly (-r loads the previously saved .qsynaptics file)

Or you can just run

> qsynaptics -r

in a console manully each time.


Nick

---

### Post by jis on 2007-10-26
In Ubuntu Gutsy you can control the click-on-tap feature in mouse settings, if I remember right. But I have forgotten how to disable it in Xunbuntu.

---

### Post by allspiritseve on 2007-11-05
I don't see any click-on-tap settings in my mouse settings, and I'm running Gutsy now. Though maybe it's because I'm running Kubuntu and not ubuntu.

---

### Post by jis on 2007-11-12
Im going to try [gsynaptics]("http://ubuntuforums.org/showpost.php?p=3754431&postcount=9")
I just don't see it anywhere in Xfce4 menus after installing it.

---

### Post by jis on 2007-11-13
There seems to be tree different GUI configuration tools for touchpad: gsynaptics, ksynaptics and qsynaptics.

---

### Post by monte48lowes on 2007-11-13
I use ksynaptics and find it works well for me in kubuntu.

Mike

---

### Post by pablosanchezuy on 2008-01-11
I use qsynaptics to disable the mousepad at login .

Edit the file  ~/.qsynaptics (that is /home/yourusername/.qsynaptics)
Find the line TouchpadOff  and add 1 at the end like this :
TouchpadOff 1
Save and quit .

Then in  System->Preferences->Session, add an entry with the command :
/usr/bin/qsynaptics --restore

At next boot, qsynaptics will run with the options in that file, and so, disabling it .

To enable, just ALT + F2 and run qsynaptics with no parameters, and use the ui to enable.

Pablo .

---

### Post by strabes on 2008-01-11
I wrote a blog post about this some time ago. It's just one line that you add into your /etc/X11/xorg.conf. [http://strabes.wordpress.com/2006/11/04/turn-off-annoying-touchpad-tap-click-in-ubuntu/](http://strabes.wordpress.com/2006/11/04/turn-off-annoying-touchpad-tap-click-in-ubuntu/)

---

### Post by Arthur Archnix on 2008-01-21
You might find my last post at the end of this thread helpful.

[http://ubuntuforums.org/showthread.php?p=4177125#post4177125](http://ubuntuforums.org/showthread.php?p=4177125#post4177125)

---

### Post by jis on 2008-05-04
qsynaptics is not available for ubuntu 8.04.

---

### Post by jis on 2008-05-04
Can you use a saved configuration by gsynaptics?

---

