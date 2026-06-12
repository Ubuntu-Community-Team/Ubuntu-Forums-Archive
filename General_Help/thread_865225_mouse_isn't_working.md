---
title: "mouse isn't working"
date: 2008-07-20
forum: General Help
---

### Post by tk03759 on 2008-07-20
Hi. I installed wminput to use my wiimote as my mouse. Everything was working fine and I could use both the wiimote or my laptops touchpad.

I restarted, and now I can't use the touchpad at all. The light is blue, meaning its been detected, but I can't use it as my mouse.

If I want to have any kind of mouse input, I have to use keyboard shortcuts to get to the terminal and start wminput to use my wiimote, but I want to use my mouse.

Can anyone help me restore the settings, or anything that would get my mouse working?

---

### Post by Darkade on 2008-07-22
I also had the same problem when setting up my wiimote as mouse.
But it's not from wiiinput, you probably installed mouseemu try stoping it with
```
/etc/init.d/mouseemu stop
```
The thing is that you'd had to do it every time you start your computer, because mouseemu starts when you boot, sorry I don't know how to prevent this, but the above command should work

---

### Post by tk03759 on 2008-07-25
Thank you. =)

I figured it out. I can't remember exaactly what I did, but I removed mouseemu, and then I used keyboard shortcuts to go into System > Preferences > and Mouse in order to turn my touchpad on.

I appreciate the help.

---

