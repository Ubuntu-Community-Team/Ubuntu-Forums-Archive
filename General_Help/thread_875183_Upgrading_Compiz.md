---
title: "Upgrading Compiz"
date: 2008-07-30
forum: General Help
---

### Post by Ataris on 2008-07-30
Can anyone tell me (without offering advice like use Synaptic or the terminal!) how to compile or whatever I need to do with the tarballs from the compiz 0.7.6 release? I must use the tarballs.

---

### Post by 16777216 on 2008-07-30
Instructions on how to compile compiz 7.6 from the git code base are found here.

 [http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

This will get a script to download the newest source files (up to the minute) and then compile and install them for you.

I recommend that you uninstall compiz if you have it installed before you run the script so you don't end up with plugins that won't activate.

---

### Post by the guitarist on 2008-07-30
> **16777216 said:**
> Instructions on how to compile compiz 7.6 from the git code base are found here.

 [http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

This will get a script to download the newest source files (up to the minute) and then compile and install them for you.

I recommend that you uninstall compiz if you have it installed before you run the script so you don't end up with plugins that won't activate.


How Can I Uninstall Compiz from my system without harming the OS? plz send me how in detail.

---

### Post by tuxxy on 2008-07-30
I personally would stick to the compiz in the repos, why do you want to upgrade?

---

### Post by 16777216 on 2008-07-30
> **the guitarist said:**
> How Can I Uninstall Compiz from my system without harming the OS? plz send me how in detail.


Removing compiz shouldn't harm the OS.
If you are referring to it wanting to remove "ubuntu desktop" that one is a meta package, it has no real files it just points to other packages to install.
Kind of like putting lettuce, tomatoes, onions, carrots, and other vegetables in a bag.
Each item has it's own name (packages) and when put to use they are called a salad (OS) but that bag (meta packages) is just the bag you brought the salad home in you can through the bag away (remove meta package) and leave out the onion (remove a "real" package) and still have a salad.

---

### Post by 16777216 on 2008-07-30
Open Synaptic in the system > administration menu and search for compiz.
Un-check everything "compiz" that is installed and click apply.

---

### Post by steveneddy on 2008-07-30
> **Ataris said:**
> Can anyone tell me (without offering advice like use Synaptic or the terminal!) how to compile or whatever I need to do with the tarballs from the compiz 0.7.6 release? I must use the tarballs.

Synaptic is point and click and the terminal is a copy/paste operation.

Compiz is already in the repos and should be installed on your system if you are using Hardy.

Why do you need 0.7.6 anyway?

It's not gonna make it look any better.

Untar the tarball and read the read me file.

---

### Post by tuxxy on 2008-07-30
To enable it you just have to to open system > prefs > appearance and select which level of compiz effects you would like enabled.

---

### Post by Cygoku on 2008-07-30
It's pointless since there is now a ppa repo, 

deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

Cygoku

---

### Post by 16777216 on 2008-07-30
> **Ataris said:**
> Can anyone tell me (without offering advice like use Synaptic or the terminal!) how to compile or whatever I need to do with the tarballs from the compiz 0.7.6 release? I must use the tarballs.

Not to mention you can't compile anything with out using the terminal, unless someone has made a "compile this for me" GUI. ( I'd pay me some money for that s***! ):lolflag:

---

### Post by steveneddy on 2008-07-30
> **Cygoku said:**
> It's pointless since there is now a ppa repo, 

deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

Cygoku

Sweet! Check it out!

I would go that way then.

---

### Post by EarloftheWest on 2008-07-31
> **16777216 said:**
> Removing compiz shouldn't harm the OS.
If you are referring to it wanting to remove "ubuntu desktop" that one is a meta package, it has no real files it just points to other packages to install.
Kind of like putting lettuce, tomatoes, onions, carrots, and other vegetables in a bag.
Each item has it's own name (packages) and when put to use they are called a salad (OS) but that bag (meta packages) is just the bag you brought the salad home in you can through the bag away (remove meta package) and leave out the onion (remove a "real" package) and still have a salad.

Excellent analogy. If you don't mind, I might use myself someday.

---

### Post by Xgen on 2008-07-31
"...pointless since there is now a ppa repo"
Thanks for the information...works just fine.

"..why do you want to upgrade?"
One reason for me is that I Iike to switch viewports instantly when left-clicking either edge side. Can't do that with the previous version as viewport switching stops at .1...which is corrected in the newest version.

---

### Post by 16777216 on 2008-07-31
> **EarloftheWest said:**
> Excellent analogy. If you don't mind, I might use myself someday.

Go right on ahead, I full of 'em. ( And most people say that ain't all I'm full of. ) :lolflag:

---

### Post by klange on 2008-07-31
> **16777216 said:**
> Not to mention you can't compile anything with out using the terminal, unless someone has made a "compile this for me" GUI. ( I'd pay me some money for that s***! ):lolflag:

[You just gave me a wonderful idea.](http://ogunderground.com/article.php?id=30)

---

### Post by Lantesh on 2008-08-01
> **Cygoku said:**
> It's pointless since there is now a ppa repo, 

deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

Cygoku

Nice!  That worked like a charm.

---

### Post by Ataris on 2008-08-03
I wasn't aware this thread was actually active...

Why do I want to upgrade? Because there are new fancy plugins and such that are for the new version. Why wouldn't I upgrade? Ubuntu is holding me back, I want the latest version.

Is there a way I can compile them without an Internet connection?

---

