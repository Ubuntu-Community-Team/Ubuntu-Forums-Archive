---
title: "Integrating FF 1.5 into the system?"
date: 2005-11-29
forum: General Help
---

### Post by Curlydave on 2005-11-29
I can run FF 1.5 by running the firefox script after downloading and unpacking it, and it works great and is very fast. However, I cannot find a way to get it to replace the default one in Ubuntu. How do I do this? Thanks! Eg, if I type in "firefox" in teh console, it loads the older one. ( I can tell because the new one shows the real FF icon in the taskbar while the old one shows the blue globe, and going to the About Mozilla Firefox options in the menu where it shows the version.)

It is interesting to note that if a copy of ubuntu-firefox is running, 1.5 will not load, as it says FF is already running. If I run 1.5 first, then open a 1.07 window by loading firefox through the ubuntu applications menu,  the 1.07 window will actually be 1.5 instead. Weird, no?

---

### Post by Curlydave on 2005-11-30
Wow, the replies got deleted?
 
Anyhow, I'm perfectly content just running it from the directory. I just replaced my shortcuts like on the desktop with a launcher that reads "/firefox/firefox". I wish I could get rid of the old, uber-slow version though.

PS: Is the new version up to speed because it's the new version, or is it because I'm running it from the directory instead of the system-integrated one?

---

### Post by ex` on 2005-11-30
It's in the wiki: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

You can always remove the old Firefox by running "sudo dpkg --remove mozilla-firefox", ofcourse. :)

---

### Post by kperkins on 2005-11-30
If you want to make it your system default got to System > Preferences > Prefered Applications, and write int the path to the executable.

---

