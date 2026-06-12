---
title: "Lenovo Ideapad Screen Artifacts"
date: 2010-08-02
forum: Hardware
---

### Post by timroberts on 2010-08-02
I'm currently using 10.04 on a lenovo Ideapad Y450. No proprietary drivers are being used on my system, but I've got a weird graphics problem. It seems as though at random intervals my screen will flicker with an artifact across an entire section of my screen. Not the whole screen, maybe a third of it or so, varying from the bottom to the middle or the top each time. Its a bit different every time. I am able to run a normal X session, and when I'm watching a movie on full screen in VLC I don't have any problems with it. I can't get any farther in hunting it down. Is anybody else having this problem? Any help is appreciated.

---

### Post by utilitytrack on 2010-08-02
Hello, would you can get few screenshots of these artifacts? Also please say which video driver you use, which version of Xserver and in which a desktop environment you work.

---

### Post by timroberts on 2010-08-03
I am unable to get a screenshot of the artifacts because I don't know when they happen and are only on screen for less than a second.

I'm running X11, with xserver 2:1.7.6 in gnome desktop environment.

My graphics driver is the default Intel graphics driver, I can't find the specific release.

---

### Post by utilitytrack on 2010-08-03
try it

```
$ dpkg -s xserver-xorg-video-intel | grep Version
```too little info so make any conclusions. I suggest to you simple record on video everything that happens on screen. Than will be more info for us and we can get an impression about artifacts' character.
[FONT=arial][COLOR=#8A8A8A]
[/COLOR][/FONT]

---

### Post by timroberts on 2010-08-03
Will do. I'll see what I can get. The intel driver I'm using is Version: 2:2.9.1-3ubuntu5. I'll post again when I've got a video of the artifacts.

---

### Post by nebajoth on 2010-08-04
Same model of laptop, same problem here.

Edit: sorry, different model.  I have the Y550.

---

