---
title: "Synaptic caches programs for install?"
date: 2008-07-13
forum: General Help
---

### Post by You bunt to? on 2008-07-13
Background: 70 years young, loosing memory, been with Dos & PC's seemingly forever. Downloaded Ubuntu 8.04 ISO file and installed same. Don't understand Bash so downloaded it through Synaptic but just as the download was being completed saw "program will be cached for install" (or words to that effect) and now I can't find it! It would be useful (for me) to be able to see the file directories in a 'tree' configuration, as seen in Windows using Explorer! The original was BASH-DOC but searches reveal nothing.

Besides 'BASH-DOC' I selected 'GRUB-DOC' (as I've already had a bad experience with Grub), and TAR-DOC (as I've downloaded Thunderbird and it sits on my desktop with a ".TAR.GZ" extension which means absolutely nothing to me).

The only good thing to come out of all this, is that I had to rush out and buy another computer, one for Ubuntu and one for Windows 2000 Pro, as Grub really screwed me.

Will [http://packages.ubuntu.com/hardy/bash-doc](http://packages.ubuntu.com/hardy/bash-doc) run in Windows?

tia
Alan

---

### Post by CatKiller on 2008-07-13
When you install a package, it is first downloaded to /var/cache/apt, then unpacked and installed. Not all programs that you install have a menu entry - some are command-line only.

bash-doc installs info files for the bash commands. Normally you would get help on those commands by typing **man <*command*>** to read the man(ual) page. With bash-doc installed, you can instead use **info <*command*>** to read the info page, which I understand is more interactive. Really, for general information and tutorials on how to use bash, Google would probably be more useful to you.

You can have Nautilus (the file manager) display a directory tree. Mine does all the time. If you've got a Nautilus window without the tree structure displayed, you can enable it with View -> Sidebar.

You don't need to download Thunderbird separately, it's in the repositories. You can simply install it with Synaptic or ```
sudo aptitude install thunderbird
``` if you prefer the command line. .tar.gz just means that it's a compressed archive. You're most likely to come across these for archives of source code, but it could be anything, similar to a .zip file.

You shouldn't, in general, need to do anything with GRUB. It's the kind of thing that just does what it does without needing manual tweaking. Perhaps something else was the problem?

---

