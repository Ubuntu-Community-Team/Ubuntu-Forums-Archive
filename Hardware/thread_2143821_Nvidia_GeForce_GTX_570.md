---
title: "Nvidia GeForce GTX 570"
date: 2013-05-10
forum: Hardware
---

### Post by silvea12 on 2013-05-10
So, this is what has happened. I removed the Nvidia 7xx binary driver from my computer, to find that unity didn't start. After that, I tried installing nvidia-current-updates, as I had done it in the past. Still didn't help.
Then I tried removing all, and still no unity.
Now, my computer won't boot properly (as in unable to access terminal for more than like 2 seconds) and it locks up trying to start lightdm. It auto logs in, so I have no idea how to change to a different window manager. Unity --replace doesnt do anything at all for me.

I need this fixed urgently, and to get my computer up and running again. I will get output of lshw when I get lynx installed for pasting stuff to pastebin.

**EDIT:** sudo lshw output: [http://paste.ubuntu.com/5650594/](http://paste.ubuntu.com/5650594/) - thanks to pastebinit

---

### Post by hil4vitkutin on 2013-05-11
```

sudo apt-get install dconf-tools

dconf reset -f /org/compiz/

setsid unity

```

[FONT=arial]Does this help? This should reset Unity.

Then try to launch Unity via terminal (just type unity). If it fails, please post the error occuring.
[/FONT]

---

