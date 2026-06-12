---
title: "Running a script when keycode is pressed e058"
date: 2015-12-01
forum: Hardware
---

### Post by ragtag on 2015-12-01
I've got a ThinkPad Yoga 12, that I'm trying to get the screen "folding" sensor to work on. In the syslog it output unknown keyode e058 and e059, and that I should use 'setkeycode e058 123' etc. to set them. Running setkeycode works (as sudo only), but I don't know where to get from there, to have it trigger a custom script.

What's a simple recipe for having keycode e058 trigger /home/ragtag/bin/myscript.py?

I'm running Ubuntu 15.10 on it.
-------

As an aside, I've gotten real close with a fully functional setup for this laptop. With everything working like it does under Windows, including detecting the orientation when in tablet mode, and automatically re-orienting the screen to match, including touchscreen and pen sensor. The only missing brick is getting the keycode for e058 and e059 to trigger my script. What I've got so far can be found [here on github]("https://github.com/ragtag/spin/tree/yoga12-2nd-gen").

Any suggestions welcome.

---

