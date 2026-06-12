---
title: "vim and python"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by ramin.honary on 2009-08-25
I am trying to get the vim application with built-in python support on my Ubuntu hardy machine.

I used synaptic to install 'vim-python', but that didn't do it. I tried 'vim-nox', and just 'vim', and still it doesn't install a python-ready vim. I don't want 'vim-gnome' or 'gvim', so I don't try installing the 'vim-all'.

However, no matter what I try, running a vim editor and entering the command
    :echo has('python')
always return false!

I am thinking of just compiling my own from source and installing it myself, but then I don't know if that will confuse 'dpkg', or make upgrading vim using 'dpkg' difficult? I've thought about removing everything except form 'vim-tiny', but wan't to avoid doing anything rash that would leave me without an editor.

Reading the package descriptions, it seems like installing the 'vim' or 'vim-nox' package should do the right thing, but it doesn't. WTF!!! I've resorted to smashing my head on the desk repeatedly. ](*,)

Can anyone tell me what's going on?

---

### Post by Mighty_Joe on 2009-08-25
Have a look [over here]("http://ubuntuforums.org/showthread.php?t=224846")

---

### Post by ramin.honary on 2009-09-01
MightyJoe, you misunderstand me.

No, I don't have any problems with indenting or editing source code. That all works just fine. I am having problems with scripting vim using python code. That is what it means to have python support built-in to the vim binary file. No matter what I install, the vim binary file I am using does not have python support, but there is source code editing support.

---

### Post by ramin.honary on 2009-09-01
[SOLVED]
Actually, I finally just uninstalled every instance of vim off of my computer using synaptic.

It turns out, the package 'ubuntu-minimal' has the 'tiny-vim' already installed. If you try to install any other 'vim' (with built-in python/perl/ruby support) on top of it, you will get all of the vim extras, including syntax hilighting and the full documentation, but it won't replace the vim-tiny binary from '/usr/bin', leaving you with the original 'vim-tiny' binary that has no built-in python support. Further, you can't get rid of vim-tiny without dissatisfying the 'ubuntu-minimal' dependency.

So I had to first uninstall 'ubuntu-minimal', which is a meta-packages so it doesn't uninstall anything, it just silences that dependency. Then I uninstalled vim-tiny. Then I re-installed 'vim-nox', which gives me the regular 'vim' with built-in python support (vim-nox runs solely on ncurses and does not have support for gtk, so it is slightly more light-weight).

Finally, after the "real" vim-nox was installed, I re-applied the 'ubuntu-minimal' meta-package. It tried to re-install 'vim-tiny', but it did not replace the already-existing '/usr/bin/vim' binary put there by the 'vim-nox' package.

So now, I have my 'ubuntu-minimal' meta-package and the version of 'vim' that I wanted.

The lesson is this: dpkg will not replace binary files existing in '/usr/bin', and synaptic won't replace anything in '/usr/bin' even if you explecitly tell it to.

---

