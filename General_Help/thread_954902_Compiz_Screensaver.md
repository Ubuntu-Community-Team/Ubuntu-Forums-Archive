---
title: "Compiz Screensaver?"
date: 2008-10-21
forum: General Help
---

### Post by higashi on 2008-10-21
Hay,

I've wanted this Compiz Screensaver ever since i first saw it on youtube. I searched the ubuntu forums many times (google too)  and im still searching but all the tutorials i tried so far ended up failing in one way or another :\

Can anyone help me out here? where can i find an accurate tutorial?  i have Compiz 0.7.6 and Ubuntu 8.04

---

### Post by loomsen on 2008-10-21
Well, there's not much of an tutorial to be done... Just get it, install, and it should be fine :)

You need these dependencies:
```

sudo apt-get install x11proto-scrnsaver-dev libxss-dev

```

Here's one repo which provides some more up to date packages:
```

deb http://ppa.launchpad.net/compiz/ubuntu intrepid main
deb-src http://ppa.launchpad.net/compiz/ubuntu intrepid main

```

if you run hardy simply replace intrepid for hardy.
Start up your software sources management, however you want to, and add both lines. Run apt-get update and you should be prompted bout available updates.

If you want it one step further, you may get shames repo instead:
```

wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./

```

This repo is usually a lil ahead compared to the official ubuntu repos.

Or you can get it from git, but... I don't think this is what you want :)

However, I installed from git yesterday, and it's still working fine, as it was before (had 0.7.9 before, from shames repo)

So, have fun :)

---

### Post by higashi on 2008-10-21
kay i followed ur instructions [not so shur i did the last step right tho]  and it didnt work P:

PS:  how do i restart compiz? [i keep having to restart my computer instead xD ]

---

### Post by loomsen on 2008-10-21
Alright, I'll specify it a lil closer.

Do this to add the sources, whichever ones you chose, to your sources.list:

```

gksu gedit /etc/apt/sources.list

```

Add the two lines for the ppa repo, if you got hardy, your sources.list should look sth like this:
```

A couple of lines which should look similar to the two you want to add...
....
....
# compiz ppa repository
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
deb-src http://ppa.launchpad.net/compiz/ubuntu hardy main

```

Just append it to the end of the file, save and close it.

Run:
```

sudo apt-get update

```

If you're not prompted about updates available you most likely already have this version installed. Otherwise you should see an orange exclamation mark...

If you rather want to add shames repo, post the first line (wget...) into a terminal to add the keyfile. Then do the steps above to add his repo to your list.
It does not make sense adding both, cause they provide pretty much the same.

I added a screenshot. You will most likely want to do it like that.

Go to the origin section, chose the list you just added, and install everything listed, except the packages you dont need (KDE-related if you run gnome, for instance)

Then you just have to log out, back in, and there you go :)

Just make sure you don't grab different versions. But I think synaptic will take care of that.

---

### Post by Mi11z on 2010-09-25
This is just what anyone will be looking for, helped me to and all of the extra third-party plugins are ace!

[http://forum.compiz.org/viewtopic.php?f=114&t=12012](http://forum.compiz.org/viewtopic.php?f=114&t=12012)

---

