---
title: "Multimediakeys of Logitech g710+"
date: 2014-05-09
forum: Hardware
---

### Post by mrksleitermann on 2014-05-09
i have a problem in Ubutu 14.04 lts with my Logitech g710+ keyboard. The problem is my multimedia keys are working in the Keyboard shortcut configuration, but they don't work correctly in the system. Many of of them doesn't work like volume up and down. The keys worked in a clean installation of ubuntu but after some time they stoped working correctly so I reconfigured it in the Keyboard shortcut configuration. Sorry for my bad bad english :D


Now i tryed to configure it with xev and Xmodmap the keycodes for the keys are 122 & 123 and when i write it down to the .xmodmap file and load it the keys doesn't work anyway.

---

### Post by mrksleitermann on 2014-05-31
I found the problem!!! gnome-settings-daemon didn't start correctly.

To my workaround.

i made a file with the following content in my user's home folder 

```
/usr/lib/gnome-settings-daemon/gnome-settings-daemon-localeexec
```

saved it and gave it permission to run with **chmod +x name-of-file**

then I opened the sudoers file with **sudo gedit /etc/sudoers** and added the following line with my username and the path to the script file to the end of the file

```
yourusername ALL = (ALL) NOPASSWD: /path/to/script
```

then i created a new entry in the startprograms and added the following text in the command entry

```
sudo /path/to/script
```

and called it **gnome-settings-daemon.**

I restarted and everithing is working just fine.

i wanted to post this because maybe someone has a similar problem

---

