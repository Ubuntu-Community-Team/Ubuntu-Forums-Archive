---
title: "suspend instead of hibernate in 12.04"
date: 2012-05-09
forum: Hardware
---

### Post by bamdad.khan on 2012-05-09
greetings,

on my laptop, pm-suspend works unreliably, i.e. sometimes it doesn't come back from sleep. thus i've always used hibernation instead, which works perfectly fine.

i usually set the gconf key 'sleep_type_ac' to 'hibernate' and i'm done.

now in ubuntu 12.04, there's no hibernate option. this is silly, but easily fixable. i can hibernate manually, but gnome-power-manager is absent from gconf-editor. i tried looking ad dconf-editor, but there aren't any applicable settings under org>gnome>power-manager.. (gods.. gtk3 and all the arbitrary changes pi$$ me the fsck off, but that is for another discussion).

so.. i can't tell the computer to hibernate instead of suspending when it's idle. does anybody know of a workaround? i would prefer not having to symlink pm-hibernate to pm-suspend or to install xfce4-power-manager. there must be a cleaner way to do something this trivial.

thanks,
bamdad

---

### Post by pastim on 2012-05-17
> **bamdad.khan said:**
> greetings,

on my laptop, pm-suspend works unreliably, i.e. sometimes it doesn't come back from sleep. thus i've always used hibernation instead, which works perfectly fine.

i usually set the gconf key 'sleep_type_ac' to 'hibernate' and i'm done.

...

so.. i can't tell the computer to hibernate instead of suspending when it's idle. does anybody know of a workaround? i would prefer not having to symlink pm-hibernate to pm-suspend or to install xfce4-power-manager. there must be a cleaner way to do something this trivial.

thanks,
bamdad

Same problem for me too.  Suspend doesn't work on my PC (it never restarts).  Hibernate works manually (I have added the tweaks to 12.04) but I cannot get it to work automatically.

---

### Post by pastim on 2012-05-18
I tripped over a solution for 12.04 whilst looking for other stuff.  Assuming you have hibernate working when you explicitly issue the command, and want it to replace 'suspend', then:

1) Install dconf Editor from the Software Centre.

2) run dconf Editor and find org > gnome > setiings-daemon > plugins > power

3) Replace 'suspend' with hibernate on whichever actions you wish - note you must scroll to near the end for the inactivity actions, such as 'sleep-inactive-ac-type'

In my case suspend doesn't work on my PC, so I changed all 'sleep' to 'hibernate'.  I also did the following to remove 'suspend' from the shutdown menu (top right)

```

sudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy 

```
Set 'allow_active' to 'no' for the suspend option.

Reboot.

---

### Post by bamdad.khan on 2012-06-01
thank you. some of it i've found over the last few weeks, but this is exactly what i've been looking for. :)

cheers,
bamdad

---

### Post by pastim on 2012-06-01
> **bamdad.khan said:**
> thank you. some of it i've found over the last few weeks, but this is exactly what i've been looking for. :)

cheers,
bamdadGlad to be of help.  I'm mostly asking for advice from others, so it's good to be able to contribute :p

---

