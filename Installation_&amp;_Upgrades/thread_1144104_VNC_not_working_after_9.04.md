---
title: "VNC not working after 9.04"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by xluryan on 2009-04-30
Well, I upgraded from 8.10 to 9.04. Here are two things I notice:

1. My wireless is incredibly less consistent. By this I mean I will lose connection several times a day. Is there any way to have it automatically try to reconnect if the connection is lost?

2. (And this is by large my biggest concern) VNC does not work anymore. I have ***always*** done the same thing: Connect to SSH, then tunnel through that for my VNC connection. I can still connect through SSH, and when I get to my box at home I can see the password screen from the screensaver, but after that, I am unable to do *anything* on the desktop. It's like no click or anything even register.

Does anyone have any ideas?

---

### Post by xluryan on 2009-04-30
Ok, just an update. It *does* register clicks. I did the following test:

- Open TightVNC and connect to my box.
- Right-click on the desktop.
- Close TightVNC.
- Reconnect via TightVNC.
- Observe the desktop has been right-clicked.

The only catch is that once you log in, the screen doesn't change. Any ideas?

Update: I've also tried with RealVNC. I get the exact same results.

---

### Post by xluryan on 2009-04-30
Ok, I've found more info. Just in case anyone else comes across this thread, here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/353126)

Hopefully this gets fixed soon. I don't want to downgrade just because of this, but I do use VNC on a daily basis. This could become quite annoying very quickly...

---

### Post by mebigfatguy on 2009-04-30
Thanks was having the same problem

[http://ubuntuforums.org/showthread.php?p=7186405&posted=1#post7186405](http://ubuntuforums.org/showthread.php?p=7186405&posted=1#post7186405)

---

