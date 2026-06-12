---
title: "A few ubuntu program isntall questions..."
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by lems on 2009-03-17
When I install a program in ubuntu through the add/remove app, where are the files stored on my system? What do I do if I want to remove a program manually(I really just want to learn about the file system lol)? Do I just delete the directory and that's it?

also, how do I remove ubuntu and install linux mint instead?

---

### Post by lloyd_b on 2009-03-17
As for the answer to your first question: ALL OVER THE PLACE.  When a program is installed by the system, parts will wind up in "/usr/bin" (executables, usually), "/usr/lib" (libraries), "/usr/share" (man pages, other docs), and potentially many other places.

Which is one reason package managers were invented :)

As for the second question, I'm not familiar with Linux Mint, but I would assume you just install using the same partitions as Ubuntu, but tell it to format the partition first, so that all of the Ubuntu data is wiped out.

Lloyd B.

---

### Post by lems on 2009-03-17
thank you lloyd! I'm guessing manual uninstall is out of the question(unless I knew where every program stored it's data).

---

### Post by lloyd_b on 2009-03-17
> **lems said:**
> thank you lloyd! I'm guessing manual uninstall is out of the question(unless I knew where every program stored it's data).

Exactly.  Unless you are *very* familiar with the program in question, odds are you'd never find all of the pieces of it.  If you install it via the package manager (add/remove software, Synaptic, "apt-get", etc), then I'd strongly recommend removing it the same way.

For this reason, if you are installing something via another mechanism (such as compiling from source), I'd recommend installing it to "/usr/local" rather than "/usr" - if necessary, you can nuke the entire "/usr/local" tree without damaging your system in in any way (though you'd lose all your manually installed software doing so...).

Lloyd B.

---

### Post by oldos2er on 2009-03-17
> **lems said:**
> When I install a program in ubuntu through the add/remove app, where are the files stored on my system? What do I do if I want to remove a program manually(I really just want to learn about the file system lol)? Do I just delete the directory and that's it?

also, how do I remove ubuntu and install linux mint instead?

 You can use Synaptic to show where each file in a package is installed. Right-click an installed package, choose Properties, Installed Files.

---

