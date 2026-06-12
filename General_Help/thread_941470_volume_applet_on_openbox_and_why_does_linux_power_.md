---
title: "volume applet on openbox and why does linux power management suck!?"
date: 2008-10-08
forum: General Help
---

### Post by Cew27 on 2008-10-08
hey guys i recently installed crunchbang linux and from the package manager then installed the battery monitor applet, this works fine although my predicted battery life is an hour less than it is in windows. but i dont know how to get the volume applet on the taskbar so i can use my volume + and - on my keyboard 
cheers

---

### Post by urukrama on 2008-10-08
I'm afraid I can't help you with the battery life. All the laptops I use are so old that they hardly have a battery life ;-)

> **Cew27 said:**
> but i dont know how to get the volume applet on the taskbar so i can use my volume + and - on my keyboard

Assuming you refer to sound volume, have a look at [this post]("http://urukrama.wordpress.com/2007/12/19/managing-sound-volumes-in-openbox/") on my blog.

You'll have to assing a keybinding to the command to lower and raise the volume. The commands are given in the above linked to blog post. On my computer, Ctrl+Up raises the volume, Ctrl+ Down lowers the volume, and Ctrl+Alt+End mutes the volume. To have this, add the following to the <keyboard> section of your rc.xml (in ~/.config/openbox/):

```
<!-- Keybindings for volume control -->
    <keybind key="C-Down">
      <action name="Execute">
        <execute>amixer -q set PCM 1- unmute</execute>
      </action>
    </keybind>
    <keybind key="C-Up">
      <action name="Execute">
        <execute>amixer -q set PCM 1+ unmute</execute>
      </action>
    </keybind>
<keybind key="C-A-End">
      <action name="Execute">
        <execute>amixer -q set PCM toggle</execute>
      </action>
    </keybind>
```

If you'd like a volume control applet in the systemtray, you can use gvtray (a link is given in the comments to the above blog entry).

---

### Post by caleb12 on 2008-10-08
There are alot of things you can do to maximize your battery life... 

[http://www.lesswatts.org/](http://www.lesswatts.org/)

That site helped me get my box configured just right. I was able to get my battery life to about the same spot as it was with Windows...

---

### Post by sdennie on 2008-10-08
As caleb12 said, [www.lesswatts.org](www.lesswatts.org) is a good starting place for battery life.  You may also want to look at: [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644) and, though probably not for your specific laptop, this thread has a lot of good information as well: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773).  If your hardware supports the power savings features in those threads/lesswatts, it's not uncommon to see nearly 50% improvement in battery life.  

However, if you are running openbox, it may not properly generate the power events (I believe they come from dbus) so, you may have to run the scripts manually or figure out how to make the events occur without using something like gnome-power-manager.

---

