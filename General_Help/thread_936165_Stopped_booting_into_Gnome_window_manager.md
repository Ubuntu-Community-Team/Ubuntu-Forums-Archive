---
title: "Stopped booting into Gnome window manager"
date: 2008-10-02
forum: General Help
---

### Post by MarcG on 2008-10-02
My wife has 8.04 running on her laptop. Yesterday the sound stopped working. Whenever playing a sound event, it would just issue clicks and "staticky" sounds. So she decided to uninstall all multimedia packages and reinstall a couple. This problem is for another topic if it comes back, but maybe something she did to "fix" the sound caused the topic of this post.

After rebooting, she now can't get the window manager to show up. The last thing we see is 
```
No resume image, doing normal boot
```
which, from doing some searching, seems to be a normal thing. But then it just boots into the command line login. When I run Firefox from the CL, I get
```
no display specified
```
My extremely limited knowledge of Ubuntu, or Linux in general, almost leads me to suspect something wrong with the X server. Maybe the window manager is also trying to come up, but there's no X to serve it? I dunno. But there are no other error messages that are related.

So is there anything I can apt-get to just get running again? Or any config files I can try to edit?

Thanks.

--Marc

---

### Post by binbash on 2008-10-02
Did she do something like hibernate suspend?

---

### Post by MarcG on 2008-10-02
> **binbash said:**
> Did she do something like hibernate suspend?

I'm guessing not. I don't think she's ever tried that and always does a normal shutdown. But I'll ask when I get home tonight.

---

### Post by whizbaby on 2008-10-02
Just reinstall the whole desktop package:
```
sudo apt-get install ubuntu-desktop --reinstall
```

(or if you installed another wm release of ubuntu you can
```
sudo apt-get install xubuntu-desktop --reinstall
```
```
sudo apt-get install kubuntu-desktop --reinstall
```
If you dont know what xubuntu or kubuntu are then you dont have that.)

Still having the sound problem?

---

### Post by MarcG on 2008-10-02
Well, something got really messed up here. Wireless stopped working, but I was able to reinstall the desktop over the wire. Reinstalling partially works. The desktop comes back and it seems to have kept her preferences, except for resolution. We're stuck with 800 X 600, or lower. I can't remember the original, but she's got a Compaq Presario laptop with a  15" widescreen.

The sound is still broken.

And she shutdown properly.

---

### Post by Sef on 2008-10-02
> but she's got a Compaq Presario laptop with a  15" widescreen.

What model?

---

### Post by MarcG on 2008-10-02
> **Sef said:**
> What model?

It's an F700.

OK, got the resolution back. I installed envyng-gtk, which reloaded the nVidia driver.

Next fix the wireless. Then onto the sounds (which started this in the first place).

---

