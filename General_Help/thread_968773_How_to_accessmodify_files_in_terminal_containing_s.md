---
title: "How to access/modify files in terminal containing space in name"
date: 2008-11-02
forum: General Help
---

### Post by frank.zappa on 2008-11-02
I was reading a tutorial on how to use the gnome-terminal and I was wondering how to access/modify files or directories with spaces in their names. Example:
```
$ cd ~/Downloads && ls
Torrent Download
Torrents
Downloads
$ rm -r Torrent Download
rm: cannot remove `Torrent': No such file or directory
rm: cannot remove `Download': No such file or directory
```In my 'Downloads' folder, there are folders 'Torrent Download', 'Torrents' and 'Downloads'. ('Torrent Download' was made using the GUI).
In this case, terminal treats it as two directories which don't exist, yielding two errors.
Now when I try to change directory:
```
$ pwd
/home/x
$ cd Downloads/Torrent Download
bash: cd: Downloads/Torrent: No such file or directory
$ cd Torrents
$ pwd
/home/x/Downloads/Torrents
```In this case, I can't change to the directory with the space in its name. I know that to solve this problem I can use underscores instead of spaces, but when trying to access something like my SD card (named 'LEXAR MEDIA') I don't want to go through the hassle of changing the name and all.

My question, is there a way to get terminal to recognize spaces in file or directory names without changing the name?

I've tried "cd Torrent*" and that seems to work, but is there any other way to do this?

---

### Post by patrickballeux on 2008-11-02
Put a "\" (backslash) before the space or enclose between "" the whole string...

---

### Post by frank.zappa on 2008-11-02
Thanks! Both of those options worked.

---

### Post by mc4man on 2008-11-02
Something you may find useful is to install nautilus-open-terminal.

It gives you a right click option 'open in terminal' on any directory and or device

---

### Post by kurtymckurt on 2008-11-03
> **mc4man said:**
> Something you may find useful is to install nautilus-open-terminal.

It gives you a right click option 'open in terminal' on any directory and or device

no offense, but i would suggest just using gnome-terminal and figuring out how to do things like go from directory to directory. It will help you a lot later when you'll want to write bash scripts. They're more than helpful for autojobs and administrating servers!

---

### Post by thestig_992 on 2008-11-03
you can also push tab when youre halfway through writing a folder / file name.
Eg, if you changing to a folder called "downloaded torrents", then you could type "cd dow" then press tab, and it will auto fill the name with a backslash included for the space. Just remember that if there are more than one folders begging with "dow", youll get a system beep and it wont work...

---

### Post by mc4man on 2008-11-03
none taken - your absolutely correct. On the other hand if i want to get to a prompt such as this or get the path to copy for use in a script (which i do with these type locations quite often) then why waste the time to type correctly

ex.
doug@doug-desktop:/media/test/Music/The Jimi Hendrix Experience (1967) Axis: Bold As Love$ 

Or if i'm building a package and moving in and out of directories it's just easier to use even though cd ./.. or cd ../..  ect. may also work. 
At some point it's more a matter of a tool that comes in handy or just plain personal choice

---

