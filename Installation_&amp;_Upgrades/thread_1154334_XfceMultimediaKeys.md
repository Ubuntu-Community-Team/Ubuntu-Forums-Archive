---
title: "XfceMultimediaKeys"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by lelik67 on 2009-05-09
Trying to make media keys Vol+,Vol-, Mute, etc. work on the laptop  with xubuntu 9.04 installed.
Following [https://help.ubuntu.com/community/XfceMultimediaKeys](https://help.ubuntu.com/community/XfceMultimediaKeys) guide.
Created .Xmodmap in the home directory with all the required keys.
Now instructions say to 
```
Go to your Xfce Menu -> Settings -> Keyboard Settings. 
Go to the Shortcuts tab and hit the left "Add" button to create your own Shortcut Profile.
```I cannot find exact path specified.
I can go ```
Applications -> Settings -> Keyboard. And then to the Application Shortcuts tab 
``` But there is no ```
left "Add" button to create your own Shortcut Profile.
``` The only "Add" button is underneath and if press it, it pops a window where I can enter a shortcut command, but  shortcut label is greyed out. If click Ok, both shortcut label (empty) and shortcut command become greyed out and the only button available is cancel?

What I am doing wrong?

---

### Post by Brandon Williams on 2009-05-09
You're doing the right thing ... when that second box pops up, just press the button that you're trying to assign a shortcut to.

---

### Post by lelik67 on 2009-05-11
Thanks. That worked. Partially.
Mute button worked and now i can mute and unmute.
Volume+ and Volume- did not work as when I press either of them nothing happens (like I never press anything).
In Terminal-> ```
xev 
``` has no events/keycodes for Volume+ and Volume-, but has events/keycodes for the Mute button.
In Real Terminal -> ```
showkey -k
``` has press/release events for the Mute button, but only press events for the Volume+ and Volume- button.

Is it a common issue? Any resolution for this?

Thanks.

---

