---
title: "Xmodmap keyboard change resets every reboot. How do I make it persistent?"
date: 2015-05-24
forum: Hardware
---

### Post by DirtDawg on 2015-05-24
I have a Lenovo laptop. The backslash/pipe key is above the Enter key but, when pressed, it inputs a '<' instead of backslash and a '>' instead of a pipe.

I can use use the command:
```
xmodmap -e 'keycode 94 = 'backslash bar'
```
to fix the problem, but any time I reboot the computer, I have to rerun the command. 

I've tried adding the command to the starting scripts (Startup Applications), I've tried making a separate '.sh' script and running *that* on startup, I've tried adding a ten second sleep timer to the script, I've tried adding the command to the ~/.xmodmap-dirtdawg file, I've tried creating a '.desktop' application file to my ~/.config/autostart directory, and I've tried adding the command to the 'xinitrc' file (both local and global). But *none* of these options work. The backslash key always reverts to the '<' sign on startup.

And yes, I've changed the keyboard setting to one of the Lenovo models that seems closest to the model I'm using. 

If anyone can tell me how to make the change stick, I would be most appreciative. I've wasted a ridiculous amount of time trying to solve this annoyance.

Thanks!

---

### Post by kryten35 on 2015-05-25
You need to create a file called  .Xmodmap  in your home directory and put the code that you posted in it. It should automatically load when you login.

To test it
```
xmodmap ~/.Xmodmap
```

Another option  would have been to add this to your .xinitrc file in home directory
```
if [ -s ~/.Xmodmap ]; then
    xmodmap ~/.Xmodmap
fi
```
In both cases you need .Xmodmap file in home directory.

---

### Post by DirtDawg on 2015-05-28
Thank you for your response and the script. 

I had actually tried modifying the .Xmodmamp file before to no avail. Tried again, but it still doesn't work. I also tried the script you provided via .xinitrc, but that also didn't stick.

I've resorted to a script on the desktop to click after login, since I'm out of ideas. Maybe I need to file a bug report. Or maybe I'm just missing something obvious. Who knows.

---

### Post by kryten35 on 2015-05-29
Its a bug.Particulary gnome based desktops.Seemingly still works in others like xfce.Been like that since 13.10.

Xmodmap not automatically loaded on start :    [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1243642](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1243642)

post #6   Has written a perl script  hack  which can be added to the startup applications.So it might be worth taking a look at that.


Otherwise your stuck with terminal  or your desktop script.Or change distro.Or wait until its fixed.

---

### Post by DirtDawg on 2015-05-30
Thanks again for the help and for finding this bug report. I can stop banging my head against the wall. I'll mark the issue as solved (even though it isn't, really!).

---

### Post by lalo on 2016-02-11
There's a good, working workaround in an Ask Ubuntu thread: [http://askubuntu.com/a/514277/99932](http://askubuntu.com/a/514277/99932)

---

