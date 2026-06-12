---
title: "installing the newest stellarium"
date: 2008-09-29
forum: General Help
---

### Post by malachi1990 on 2008-09-29
So I like stellarium, and tried to install the newest version, only to find that the directions (found here: [http://stellarium.org/wiki/index.php/Compilation_on_Linux](http://stellarium.org/wiki/index.php/Compilation_on_Linux) ) didn't work for me.  

So I made it a deb file, which sticks everything into my / folder, a bad idea, I know (but it was my first attempt creating a deb file).  Didn't matter, because the computer couldn't find the program start prompt.  So I had to uninstall this particular version anyways.

So does anyone know how to install the newest stellarium?

Many thanks.

P.S.  If this is in the wrong forum, I apologize.

---

### Post by snova on 2008-09-29
I love Stellarium! Unfortunately, I've already tried...

[LIST=1]
  [*] There is no .deb for stellarium in the repos yet, because it's only been out for a few weeks.
  [*] Compiling from source is the only way to get it for now.
  [*] It depends on a very recent version of Qt that isn't in the Hardy repos yet, not even in backports. This is another reason there is no deb.
[/LIST]

So unless you want to enable Intrepid repositories, you're stuck.

Sorry. I suggest you try the Windows binary with Wine, but as I only just thought of that and as such haven't tested it myself, the results might be awful.

---

### Post by malachi1990 on 2008-09-29
As I said, I was creating the deb myself.  Didn't too well, but at least it compiled.

Thanks for the tips.

---

