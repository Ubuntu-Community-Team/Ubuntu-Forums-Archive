---
title: "Multiple annoying problems after upgrade"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by yesint on 2009-04-29
Dear All,
After upgrade to Jaunty I experience a lot of small, but annoying problems. I would be grateful if somebody could help me 

1) Something is wrong with update notifications. Instead of the message in notification area the update window pops up all the time. Even if close it it pops up again after each login. Very annoying.

2) I can't figure out why the indicator applet is needed. It sits in the panel together with the pidgin icon and duplicates blinking of this icon. Probably I missed something... Is it possible to remove it without breaking something with notifications?

3) During the boot the resolution of the splash screen is very low (probably 800x600), while in 8.10 it was correct

---

### Post by halovivek on 2009-04-29
Give these in terminal and try again
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by yesint on 2009-04-29
The system is freshly upgraded. This seems to be "features" of 9.04... Any ideas how to get rid of them?

---

### Post by mgmiller on 2009-04-30
> 1) Something is wrong with update notifications. Instead of the message in notification area the update window pops up all the time. Even if close it it pops up again after each login. Very annoying.It's not a bug, it's a feature!
There was a huge go around in the bug reporting area about this and Mark Shuttleworth himself, chimed in.  This is how they are doing this from now on, so deal with it.....

Well, this is linux, so you can change it if you want.

run the gconf editor
```
gconf-editor
```On the left side, click the triangle next to "apps" to expand the list.
Scroll down till you see  "update-notifier".  Click once to high lite it.

On the right side, uncheck where it says "auto_launch"
and then click on "regular_auto_launch_interval" and change it from 7 to 0 (that's the number zero, not the letter o)

You can then close down the gconf-editor. 

This should return you to the original behavior of an icon in the top panel, instead of having the update manager window open in your face every time there is an update available.

> 2) I can't figure out why the indicator applet is needed. It sits in the panel together with the pidgin icon and duplicates blinking of this icon. Probably I missed something... Is it possible to remove it without breaking something with notifications?This is part of your first question.  I think it may blink if something needs your attention.  You can safely remove it if it bothers you.  

It's easy to add back in if you seem to be missing something, just right click on a blank area of the panel where you want it to be and select add to panel.  You'll find indicator applet in the list, click it and then click "add".


> 3) During the boot the resolution of the splash screen is very low (probably 800x600), while in 8.10 it was correct

You can install the startup manager which will let you tweak this setting.

```
sudo apt-get install startupmanager
```

---

### Post by yesint on 2009-05-01
> **mgmiller said:**
> It's not a bug, it's a feature!
There was a huge go around in the bug reporting area about this and Mark Shuttleworth himself, chimed in.  This is how they are doing this from now on, so deal with it.....

Well, this is linux, so you can change it if you want.

run the gconf editor
```
gconf-editor
```On the left side, click the triangle next to "apps" to expand the list.
Scroll down till you see  "update-notifier".  Click once to high lite it.

On the right side, uncheck where it says "auto_launch"
and then click on "regular_auto_launch_interval" and change it from 7 to 0 (that's the number zero, not the letter o)

You can then close down the gconf-editor. 

This should return you to the original behavior of an icon in the top panel, instead of having the update manager window open in your face every time there is an update available.

This is part of your first question.  I think it may blink if something needs your attention.  You can safely remove it if it bothers you.  

It's easy to add back in if you seem to be missing something, just right click on a blank area of the panel where you want it to be and select add to panel.  You'll find indicator applet in the list, click it and then click "add".




You can install the startup manager which will let you tweak this setting.

```
sudo apt-get install startupmanager
```

Thanks a lot!

---

