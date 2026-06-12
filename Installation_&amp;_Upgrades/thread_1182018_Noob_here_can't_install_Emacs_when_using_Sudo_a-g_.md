---
title: "Noob here can't install Emacs when using Sudo a-g install..."
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by Noobuntu5 on 2009-06-08
I can get into VI no problem but trying to sudo apt-get install emacs22 I get a couldn't find package???

I did the Wubi install on my Vista Home. I see the etc/emacs folder, but im stumped. any help appreciated. 

I just prefer the emacs to vi.

---

### Post by unutbu on 2009-06-08
Open a terminal (Applications>Accessories>Terminal) and type
```

dpkg --get-selections | grep emacs
```

This will show all the emacs-related packages that you currently have installed. 

Then run
```

sudo apt-get install emacs22
```
and show us the error message.

Please also indicate what version of Ubuntu you are using (e.g. Jaunty?)

Once we know what you have installed, we'll know better what's needed to get emacs working for you.

Could I also make a suggestion? You might want to install emacs-snapshot instead of emacs.
emacs-snapshot (which is also in the official repos) allows you to use ttf fonts instead of the chunkier fonts available under emacs.

---

### Post by Noobuntu5 on 2009-06-08
angel@ubuntu:~$ dpkg --get-selections | grep emacs
angel@ubuntu:~$ sudo apt-get install emacs22
[sudo] password for angel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emacs22
angel@ubuntu:~$ 

Using Jaunty thank you

---

### Post by Noobuntu5 on 2009-06-08
Same thing happens with snapshot

Would love to try emacs-snapshots...

---

### Post by unutbu on 2009-06-08
Click System>Admin>Software Sources. Under the first tab, entitled "Ubuntu Software",
make sure you have the "Community-maintained Open Source software (universe)" checkbox enabled. While you are there, you might as well also enable any other repos you are interested in.

Close the window. Your package database should automatically be updated, but just to make sure, in the terminal, type
```

sudo apt-get update
```

This will definitely refresh the package database on your machine.

Then try ```


sudo apt-get install emacs-snapshot

```

---

### Post by Noobuntu5 on 2009-06-08
That did it thank you for your help and your suggestions. :p

Got vim running as well sweet.

---

### Post by unutbu on 2009-06-08
Terrific. Now to setup a default ttf font, all you need to do is put something like
```

(set-default-font "Monospace-12")
```
in your ~/.emacs file.

---

### Post by Noobuntu5 on 2009-06-08
are you saying to create the file into the etc/emacs-snapshot folder or add it to the 00debian-vars.elc? I is a lil confoosed on that.

---

### Post by unutbu on 2009-06-08
"~/.emacs" means the .emacs file in your home user directory. The tilde is a shorthand notation (understood by the shell) for your home user directory.

If you don't have this file, create it. (You can create it using emacs :))

Note that if you use Ubuntu's default file browser (Nautilus), you may have to press
Ctrl-h to see so-called "dot files" (i.e. files or directories that start with a period).
Dot files are hidden by default.

When you run emacs-snapshot it will look for and read your ~/.emacs file. You can put all your customizations in there.

---

### Post by Noobuntu5 on 2009-06-08
got it! very cool thank you for your help.

---

### Post by unutbu on 2009-06-08
No problem! Enjoy emacs and Ubuntu. :)

---

