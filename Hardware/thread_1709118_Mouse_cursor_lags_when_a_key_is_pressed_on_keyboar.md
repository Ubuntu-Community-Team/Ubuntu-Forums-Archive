---
title: "Mouse cursor lags when a key is pressed on keyboard in 10.10, using a touchpad.10"
date: 2011-03-17
forum: Hardware
---

### Post by romwell on 2011-03-17
If I press any key on the keyboard when the mouse cursor is moving, the cursor stops for half a second then jumps to the correct position.

If any key is pressed while I am not touching the touchpad, then input from touchpad is ignored for half a second or so.

This is especially annoying in browsing web pages, since I can't effectively Ctrl+Click or Shift+Click pages. I have to hold down a key, wait, then click.


A [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/503041") for a similar issue has been on Launchpad since 10.04, apparently.

Some potential solutions that **do not work **for me:

- "Disable touchpad while typing" option is unchecked in Mouse options;
-  mouseemu package which have been causing this problem for some users has never been present on the system.

The system is an Asus EeePC 1000HE with Elantech toucpad, with EeePC-related packages (Jupiter) installed running Ubuntu 10.10. 

System report is attached to this post.

Any help will be greately appreciated :)

---

### Post by romwell on 2011-03-18
OK, I have found the cause! Syndaemon is responsible for this behavior.
Killing syndaemon solves the problem until the next logon.

That is, running 

```
killall syndaemon
```

in the terminal restores normal mouse behavior. 

Now if someone knew why the Mouse preferences option does not work...

---

