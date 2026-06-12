---
title: "Permissions, command lines and starting programs"
date: 2008-11-03
forum: General Help
---

### Post by invalidusername on 2008-11-03
Hello everyone, I just have a few quick basic questions.

I've been using Windows my entire life so I guess I've become accustomed to certain things. When I install a program in Windows it leaves a handy little icon on the desktop so that when I want to use it all I have to do is click. Apparently it doesn't work this way in Linux. I tried installing a program in Ubuntu from the Synaptic Package Manager called "Astrolog" (yes I'm into astrology). It installed fine...I think. But I can't figure out how to run the program. Eventually I found the executable stored in the root somewhere but then it told me "I don't own the program so I can't use it". So, I use that "sudo chown" command line to give me root privileges and it still doesn't let me double click to execute it. It gave me the privilege to edit the properties of the file but double clicking on it doesn't do anything.

So I have a few questions. How would I start this program, or any other program loaded from the Synaptic Package Manager for that matter? Why would I need special privileges to run this program or any other for that matter on my computer.

It's seriously irritating to have to enter a password or acquire special privileges every time I want to run a program. Is there some way around this? I want to like this OS so badly, it has so much going for it but sometimes I wonder if it's really worth it.

---

### Post by geirha on 2008-11-03
GUI applications normally get a menu entry when you install them from the repositories (which you did). However, astrolog is not a GUI application, it's a command line application, so open up a terminal and type astrolog. 

You can use the command ```
dpkg -L *packagename*
``` to see which files a package installs. In synaptic you'll find the package-list by right-clicking the package, selecting properties then look at the «installed files» tab.

```
user@ubuntu-desktop:~$ dpkg -L astrolog
/.
/usr
/usr/games
/usr/games/astrolog
/usr/share
/usr/share/doc
/usr/share/doc/astrolog
/usr/share/doc/astrolog/README.540.gz
/usr/share/doc/astrolog/README.1ST
/usr/share/doc/astrolog/Update.540.gz
/usr/share/doc/astrolog/astrolog.cgi.gz
/usr/share/doc/astrolog/fixplaces
/usr/share/doc/astrolog/README.Debian
/usr/share/doc/astrolog/copyright
/usr/share/doc/astrolog/changelog.Debian.gz
/usr/share/doc/astrolog/Helpfile.540.gz
user@ubuntu-desktop:~$ astrolog
** Astrolog version 5.40 (See '-Hc' switch for copyrights and credits.) **
   Invoke as 'astrolog -H' for list of command line options.
Enter month for chart (e.g. '8' 'Aug') > 

```

---

### Post by invalidusername on 2008-11-03
> **geirha said:**
> GUI applications normally get a menu entry when you install them from the repositories (which you did). However, astrolog is not a GUI application, it's a command line application, so open up a terminal and type astrolog. 

You can use the command ```
dpkg -L *packagename*
``` to see which files a package installs. In synaptic you'll find the package-list by right-clicking the package, selecting properties then look at the «installed files» tab.

```
user@ubuntu-desktop:~$ dpkg -L astrolog
/.
/usr
/usr/games
/usr/games/astrolog
/usr/share
/usr/share/doc
/usr/share/doc/astrolog
/usr/share/doc/astrolog/README.540.gz
/usr/share/doc/astrolog/README.1ST
/usr/share/doc/astrolog/Update.540.gz
/usr/share/doc/astrolog/astrolog.cgi.gz
/usr/share/doc/astrolog/fixplaces
/usr/share/doc/astrolog/README.Debian
/usr/share/doc/astrolog/copyright
/usr/share/doc/astrolog/changelog.Debian.gz
/usr/share/doc/astrolog/Helpfile.540.gz
user@ubuntu-desktop:~$ astrolog
** Astrolog version 5.40 (See '-Hc' switch for copyrights and credits.) **
   Invoke as 'astrolog -H' for list of command line options.
Enter month for chart (e.g. '8' 'Aug') > 

```

I think I understand now. Thank you very much for the help.

---

