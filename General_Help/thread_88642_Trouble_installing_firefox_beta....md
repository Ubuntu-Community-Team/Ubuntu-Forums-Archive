---
title: "Trouble installing firefox beta..."
date: 2005-11-10
forum: General Help
---

### Post by allroz on 2005-11-10
Nevermind about that. I just "installed" it and when i go to run it, it says i have a problem with my chrome registries. I removed totem, (im not sure about the plugin though) , installed the mozilla-mplayer, as well as the package 'libstdc++d' and followed the instructions. When i go to run i though, i get a massive amount of errors. If it would help i posted them, ill install it again and then paste it.

---

### Post by teaker1s on 2005-11-10
just download the tarball use ark to untar it (click on tar file) and then click the installer in the file and it installs
or if you prefer konsole(terminal) you need to cd into your directory eg     cd/home/teaker1s/desktop
tar -zxvf yourfile.tar.gz and then run the installer

explanation of tar below
[untar]("http://simplythebest.net/info/unix/untar.html")

---

### Post by allroz on 2005-11-10
Sorry, Edit.

---

### Post by teaker1s on 2005-11-10
chrome is the effect that firefox and thunderbird use-keep a backup of any data and bookmarks then delete mozzilla directory you should be able to find it's location on mozzilla.org or use google-I'm sorry I can't suggest more

good luck

---

### Post by allroz on 2005-11-10
Hmm. Can you be more specific on how to delete the mozilla directory? I think i know what you're saying, but don't want to break my installation.

---

### Post by allroz on 2005-11-11
Anyone have any ideas? When i go to run it it just takes me to the feedback manager and says to consult the person who created it. I've installed those packages and followed those directions, but i have not removed any directories. Am i supposed to? Also, i havn't removed 1.07 before i install. I've tried to, but then i can't install beta. Help?

---

### Post by jrib on 2005-11-11
I'm not sure if there is more going on here but I was assured in the official firefox irc channel that chrome registration errors were "normal/expected" when you first run the beta (something about seamonkey compatability although I'm not sure how/why).  I got them as well, but after closing firefox and starting it backup they went away.  They also pop up when I install a new extension, but everything works fine.

---

### Post by teaker1s on 2005-11-11
If firefox will run I'd install a different theme-if on the other hand it won't then uninstall firefox and follow the link below- clear the residual settings and then reinstall firefox

[http://www.mozilla.org/support/firefox/edit]("http://www.mozilla.org/support/firefox/edit")

---

### Post by allroz on 2005-11-11
The problem is that firefox will not run at all. I just get the qulity agent feedback report thing when i attempt to run it. Although i can run 1.07 when i type in "mozilla" into a terminal, i can't run 1.5 when i type "firefox" into the terminal.

---

### Post by canadianwriterman on 2005-11-11
[QUOTE=allroz]The problem is that firefox will not run at all. I just get the qulity agent feedback report thing when i attempt to run it. Although i can run 1.07 when i type in "mozilla" into a terminal, i can't run 1.5 when i type "firefox" into the terminal.[/QUOTE]

I had a lot of difficulty installing Firefox 1.5 and getting it to work until I followed this Wiki instruction sheet:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

It's very finicky, but perhaps if you reinstalled and followed the sheet really carefully it might solve your problem. Worth a try.

---

### Post by allroz on 2005-11-11
That's what i've been trying to install it off of.

---

### Post by allroz on 2005-11-11
Hmmm. This is really stumping me. Am i supposed to write over a directory.

---

### Post by briguy on 2005-11-12
You can delete or rename the folder .mozilla (the period is important) in your home directory.  Go into terminal, run:

mv .mozilla .mozilla.orig

When you start Firefox 1.5 (or any version for that matter) it will make a new .mozilla directory from scratch.  You won't have any of your old bookmarks, extensions etc.  To get plugins working, go to the /firefox/plugins/ directory where you installed 1.5 and run:

sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

For more info, try this thread: [http://www.ubuntuforums.org/showthread.php?t=86973&highlight=firefox+1.5+plugins](http://www.ubuntuforums.org/showthread.php?t=86973&highlight=firefox+1.5+plugins)

---

### Post by bluevoodoo1 on 2005-11-21
[QUOTE=allroz]Nevermind about that. I just "installed" it and when i go to run it, it says i have a problem with my chrome registries. I removed totem, (im not sure about the plugin though) , installed the mozilla-mplayer, as well as the package 'libstdc++d' and followed the instructions. When i go to run i though, i get a massive amount of errors. If it would help i posted them, ill install it again and then paste it.[/QUOTE]

I'm having a similar problem with Chrome registries... I get a message about that before I start firefox, but then FF works fine. I have not deleted totem because it is named "ubuntu-desktop" in Synaptic and I am afraid something terrible might happen if I do delete it! (I'm a new user). I did follow much of what was said [http://www.mozilla.org/support/firefox/edit](http://www.mozilla.org/support/firefox/edit) and [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) 

Also I think I might not have deleted the previous release of FF as I have a ".mozilla" and ".mozilla.ubuntu" file folders. Is this significant? Should I get rid of one of them?

---

