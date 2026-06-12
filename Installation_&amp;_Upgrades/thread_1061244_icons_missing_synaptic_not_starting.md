---
title: "icons missing/ synaptic not starting"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by cholericfun on 2009-02-05
Hi.

I have a problem with some programs such as firefox and gedit not showing some icons, what i find really inconvenient is that synaptic package manager does not start at all, I am still able to use the command line, but i'd rather have a fixed system...

basically the problem seems to be gtk-...png files beeing corrupt. 
Just in case - heres some history of what i did:

i have a dual boot Win XP and Ubuntu 8.04 on seperate partitions.
recently my Win hung up because of a corrupt Google.updater file and i had to Reset the computer a lot of times trying to fix it (its now more broken than ever i think...). Among other things i tried going into the Windows partition via Ubuntu to remove the broken files. Ubuntu could not mount the C partition because it was not shut down properly. Trying a force mount just resulted in Ubuntu hanging up (i tried ctrl-alt-F4 and had error messages flickering all over the screen without any chance of typing anything)
so i bothered the reset buttom again,
since then i have the abovementioned problems.

e.g. typing "gedit" into the shell i get ... gedit and a few warnings such as:

(gedit:16488): Gtk-WARNING **: Error loading theme icon 'gtk-new' for stock: Failed to open file '/usr/share/icons/Human/24x24/actions/gtk-new.png': No such device or address

(gedit:16488): Gtk-WARNING **: Error loading theme icon 'gtk-open' for stock: Failed to open file '/usr/share/icons/Human/24x24/actions/gtk-open.png': Permission denied

the more annoying bit is synaptic:
typing
  sudo synaptic package manager
i get
(synaptic:16537): Gtk-WARNING **: Error loading theme icon 'gtk-refresh' for stock: Image file '/usr/share/icons/Human/24x24/actions/gtk-refresh.png' contains no data

albeit without any return-to-comand, and without any synaptic...
i have to ctrl-c to get back into the shell

i tried reinstalling firefox but apt-get purge firefox didnt succeed in getting rid of it (it still worked but i could reinstall it), same problem as before...

So...
what to do???

Can I get these Images again from somewhere (where) and just replace them?
and why are they getting broken (in view of avoiding future problems...)

Thanks to all for your ideas and help!

Leo

---

### Post by cholericfun on 2009-02-05
Ok, 
i guess writing it down helped...
booting with the live cd and copying the folder over with the damaged pics did the trick,
also recovery did a lot of work when i ran it, (doing an "fsck" keeping "y" pressed for a long time)
aldeady seemed to do half the trick (gedit opened completely and without errors, synaptic still wouldnt do it)

still find it strange such a thing happens, but ah well, theres other things to worry about...

---

