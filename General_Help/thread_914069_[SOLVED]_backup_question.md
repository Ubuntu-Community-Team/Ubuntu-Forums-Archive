---
title: "[SOLVED] backup question"
date: 2008-09-08
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2008-09-08
I want to backup new or changed files in one directory to a usb drive on /media/LEXAR. So that I don't have to remember everything I've done, it would be good to have a command that I can run in a terminal to check the directory that I'm in against the lexar drive's contents. Does anyone know how to do this?

---

### Post by skullmunky on 2008-09-08
there are probably more ways to do this than you can count :)

If you use KDE, there's the program "Keep", which is a backup manager.  There is probably a similar one in Gnome; that'd be the easiest.

Or, from the command line, you could try the "rsync" (remote sync) command.  It does synchronized backups over the network, but also just to other directories or drives.  rsync is ridiculously powerful, so look around for a tutorial on doing simple things with it.  it's probably something like this:

rsync -avz /home/skullmunky /media/LEXAR

if you just want to compare the contents of two directories, there's probably some way of finagling that with the "diff" command.

---

### Post by HermanAB on 2008-09-08
Rsync is your friend.

---

### Post by anotherdisciple on 2008-09-08
I would man Rsync or look [[COLOR="Blue"]here[/COLOR]]("http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=r/rsync")

---

### Post by ihatetryingtopickaloginna on 2008-09-08
Rsync looks like what I need. Thanks guys.

---

