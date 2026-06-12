---
title: "when i upgrade to 9.10 will it save my settings etc?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by bilmas on 2009-10-15
when i upgrade to 9.10 will all my settings and software continue to work even if they happen to be built for the 9.04 architecture?

for example: i got boxee working in 9.04 64-bit and it'd be great if that continued to work

i just hope i don't have to start from scratch for everything.

---

### Post by earthpigg on 2009-10-15
in theory, yes.

historically, in-place upgrades dont quite work correctly for about 10% of users (i pulled that figure out of thin air -- its a *guess*timate...).

some of the new under-the-hood features of 9.10 will only be implimented on fresh installs, and not on upgrades. a 9.10 fresh install will likely be a smoother system than a 9.04 upgraded to 9.10 system.


i personally always do fresh installs.


here's a handy piece of information:

all program settings are kept in your /home/username folder. in the file manager, select view -> hidden files and folders.

everything starting with a dot (".")? thats called a dotfile. it contains the settings for a specific program.

when you feel like it, explore the folders and files, especially for programs you use a lot.

if you back those up, do a complete fresh install, ***and then put those dotfiles back where you found them on your old install***, then your settings will all be restored the next time you log in or (re)start a given application.

some backup/restore ***all*** their dotfiles on a fresh install, some people (like me) do it ***selectively***.... really, i usually just restore firefox (the .mozilla folder), pidgin (the .purple folder), and my .bashrc dotfiles.... and keep all the rest around for a week so they are available if i decide i want to use them.

---

