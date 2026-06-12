---
title: "[SOLVED] [BASH][grep] help me craft my regular expression."
date: 2008-09-13
forum: General Help
---

### Post by MaxIBoy on 2008-09-13
I'm trying to reinstall all packages with libgl in the name. I'm doing this with an "apt-cache search" command which outputs to a file, then a grep command that isolates only the names of the packages with libgl *actually in the name*, and without the descriptions. The grep command's output is then used in an "apt-get install --reinstall" command.

I'm getting stuck at the grep command. Here's what I've got:
```
maxtothemax@maxtothemax-desktop:~$ sudo apt-cache search .libgl.>pkgs
maxtothemax@maxtothemax-desktop:~$ grep -o ^.*libgl[^[:space:]]* pkgs
libgl1-mesa-dev
libgl1-mesa-dri
libgl1-mesa-dri-dbg
libgl1-mesa-glx
libgl1-mesa-glx-dbg
libgl1-mesa-swx11
libgl1-mesa-swx11-dbg
libgl1-mesa-swx11-dev
libgl1-mesa-swx11-i686
libglade2-dev - development files for libglade
libglademm-2.4-1c2a - C++ wrappers for libglade2
libglademm-2.4-dbg - C++ wrappers for libglade2
libglademm-2.4-dev - C++ wrappers for libglade2
libglademm-2.4-doc - C++ wrappers for libglade2
libglew1.5
libglib-perl
libglu1-mesa
libglu1-mesa-dev
guile-gnome0-gtk - Guile bindings for GTK+, libglade,
libghc6-glade-dev - A GUI library for Haskell (Gtk2Hs) -- libglade
libglade2-ruby
libglade2-ruby1.8
libglui2c2
libglib2.0-dev
libglib2.0-doc
maxtothemax@maxtothemax-desktop:~$ 

```
As you can see, my regular expression isn't catching all the package descriptions, for instance the ones for libglade-related stuff. What am I doing wrong?

---

### Post by Pro-reason on 2008-09-13
You don't need such a complex regular expression.  You just need a space, a dot and an asterisk to strip out everything after the first word.

```
sudo apt-cache search .libgl. | **sed "s/ .*//"** | grep libgl
```

In fact, you can even do it without regular expressions at all:

```
sudo apt-cache search .libgl. | **awk '{print $1}'** | grep libgl
```

Hope that helps.

P.S. Either method takes about six or seven seconds to print the results on my machine.

---

### Post by Pro-reason on 2008-09-14
I'm concerned that the initial command (*sudo apt-cache search .libgl.*) is wrong.  The list it returns doesn't seem to properly correspond to what I have installed.

---

### Post by MaxIBoy on 2008-09-15
Apt-cache searches the repos, not what you've got installed. That's okay, because apt-get install --reinstall ignores packages you don't already have.


Thanks for the help.

---

### Post by Pro-reason on 2008-09-15
> **MaxIBoy said:**
> That's okay, because apt-get install --reinstall ignores packages you don't already have.


Hmm.  I've just tried it on a package that is not installed, and it installed it!  Where did you get that info from?

---

