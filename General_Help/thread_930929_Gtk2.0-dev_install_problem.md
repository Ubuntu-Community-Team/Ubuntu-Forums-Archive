---
title: "Gtk2.0-dev install problem"
date: 2008-09-26
forum: General Help
---

### Post by dfrandin on 2008-09-26
I'm trying to set up to build a custom kernel, I have the source, build-essentials, etc, and would like to use the nice menu-config, which seems to be listed as gconfig. When I do a 'make gconfig' I get 

* Unable to find the GTK+ installation. Please make sure that
* the GTK+ 2.0 development package is correctly installed...
* You need gtk+-2.0, glib-2.0 and libglade-2.0.

I'm told all that lives in the libgtk2.0-dev package, which, causes me the attached screenshot in Synaptic when I attempt to install it...  

I have ALL repositories enabled, and still get the screenshot error...

Help!!

Am on Ubuntu 8.04....

Dave

---

### Post by mc4man on 2008-09-26
There error is saying you have libgtk2.0-0 (2.12.9-4ubuntu3)  which is not an ubuntu version.
You must have gotten it from somewhere else, probably with some other packages which may be dependent upon it. The proper one is ....-3ubuntu4 (for an updated hardy, ...-3ubuntu2 when it first released.

Do you know how you acquired it?

see here for similar and general idea
you should be able to *force* the version back in synaptic after identifying any 4...3 dependent packages (if any

[http://ubuntuforums.org/showthread.php?t=822068](http://ubuntuforums.org/showthread.php?t=822068)

---

### Post by dfrandin on 2008-09-27
Thanks for the reply... Not a clue where I picked it up from.. I'm not into gtk programming, but to run the gconfig kernel config menu, it says I need the dev piece.. I tried installing the deb link you gave me for the correct version... Says I have a newer version... Someone in the other thread mentioned something about forcing.. I assume thats done via apt-get and overrides the install and puts the correct version on?? 


Dave

---

### Post by mc4man on 2008-09-27
try opening synaptic, search libgtk2.0, then highlight the package and in the top panel under the package tab should be a force version option. In the popup choose the hardy ver.

---

### Post by dfrandin on 2008-09-27
Synaptic doesnt show libgtk2.0-dev installed, but if I try to install it, I get the same error in my original screenshot... Whatever version of the gtk2.0-development library that is on here, doesnt seem to show up in Synaptic for me to uninstall... Since all I need this library for is to configure a kernel build with gconfig, and since I have the gtk-dev library installed on another system, I think I'll just make my kernel config file over there and perhaps build the kernel over there too, since its a MUCH faster machine than this laptop.. I'd wanted to build the kernel on the laptop since thats the machine thats gonna run the new kernel... oh well... doncha love dependancy hell!!

Thanks for the assist...

Dave

---

### Post by mc4man on 2008-09-27
> search libgtk2.0

you should have been looking for *libgtk2.0* and trying to force that (libgtk2.0) back to the hardy version. Then you would be allowed to install libgtk2.0-dev

---

### Post by dfrandin on 2008-09-28
I mistakenly attempted to do just that, and was promptly warned with about a page long list of stuff that would be uninstalled if removed libgtk2,0..
If I selected the libgtk2.0-0 (2.12.9-4ubuntu3) and did a package/force, I got a picklist that showed a 2.12.9-4ubuntu3 (now) and two choices of 2.12.9-3ubuntu4 (hardy-updates) and 2.12.9-3ubuntu2 (hardy). I tried forcing it the 2.12.9-3ubuntu4, which I understand is the one I need, but I get the same long list of stuff to be uninstalled...

Update: While snooping around in Synaptic, I noticed, under the "Installed (local or obsolete) all the programs like opera, skype, truecrypt, webmin that I'd installed via dpkg, but there was listed libgtk2.0-0, libgtk2.0-bin, and libgtk2.0-common...

---

### Post by mc4man on 2008-09-28
If you can't force the version 'cleanly' then certainly don't try and wait for some further advice. While it may not matter, it wouldn't hurt if you could figure out what app installed the patched libgtk2.0-0, libgtk2.0-bin, and libgtk2.0-common packages.

---

### Post by Ptero-4 on 2008-09-28
do you have the getdeb repository enabled? Maybe you can reload your repositories list by typing "aptitude update" at the terminal or clicking reload in synaptic, maybe the -dev package catches up with the rest of gtk2.

---

### Post by mc4man on 2008-09-28
It going to depend on what's being removed as to whether you should force the version.
Not knowing what you installed to cause the 'upgrade' to the patched versions (libgtk2.0-0; libgtk2.0-bin) I could only install them and then force the downgrade to hardy-updated. In this case there were very few packages removed, none 'critical', and the force went well. The removed packages were easy to reinstall. (mainly centered around ubuntu-desktop


> Commit Log for Sun Sep 28 14:01:49 2008

Downgraded the following packages:
libgtk2.0-0

Removed the following packages:
gnome-themes
gtk2-engines-pixbuf
gtk2.0-examples
gucharmap
libgtk2.0-bin
ubuntu-desktop

Commit Log for Sun Sep 28 14:03:42 2008

Installed the following packages:
gnome-themes (2.22.0-0ubuntu1)
gtk2-engines-pixbuf (2.12.9-3ubuntu4)
gucharmap (1:2.22.1-0ubuntu2)
libgtk2.0-bin (2.12.9-3ubuntu4)
ubuntu-desktop (1.102)

If you could post what's being removed or figure out the app that caused this that would be helpful.

---

