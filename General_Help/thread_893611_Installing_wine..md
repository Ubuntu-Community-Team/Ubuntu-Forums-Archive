---
title: "Installing wine."
date: 2008-08-18
forum: General Help
---

### Post by Uner on 2008-08-18
Yeah, before starting, I wanna say that I'm a total Ubuntu noob (any linux noob, in fact..). 
I'm trying to install Wine right now, but I simply can't... I get alot of errors.

I tried installing with Add/Remove, and I got..

```
'Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.'
```


I tried installing with Synaptic package manager, and I got...

```
'wine:
 Depends: libaudio2  but it is not installable
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
 Depends: winbind  but it is not installable
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed'
```

I tried using the terminal, and typed in - sudo apt-get install wine, and it did something, and I just remember the last line.. 

'E: Broken Packages'

I just tried the code again, and got

'E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?'

What does 'depends' mean in ubuntu slang?
I really need help, I'm totally desperate. I did google for solutions, but didn't find any.

---

### Post by Ryadt on 2008-08-18
Try restarting x - Ctrl+Alt+Backspace. Then retry the installation.

---

### Post by Elfy on 2008-08-18
Do you have your software sources set up - System >Admin menu.

Check multiverse, universe, restricted and main enabled, disable cdrom. 3rd party tab - partners.

---

### Post by Uner on 2008-08-18
Ryad - Restarted Ubuntu, nothing changed, same error.
forestpixie - System -> admin menu? I don't have that. Software sources set up? I don't even know that means, as I said, I just started using Ubuntu last night.

By the way, I'm using Ubuntu 7.10.

---

### Post by Elfy on 2008-08-18
You don't have an admin option in the system menu? What menus do you have on your top panel?

Assuming you find it - open the software sources - there are 4 tabs - the first 4 I give should be on the first tab, tick all those I have given, remove tick from the cdrom box. On the 3rd party tab - enable the partners.

If you don't have menu on the panel - what does it look like, maybe a screenshot

[http://ubuntuforums.org/showpost.php?p=4527031&postcount=4](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4)

---

### Post by gjoellee on 2008-08-18
***Systems->Administration->Software Sources***

and do what Forestpixie tells you...

---

### Post by Uner on 2008-08-18
Oh, I see, thanks alot. Let me try installing wine now, I'll edit my post with the results. :)

now I get...

Could not mark all packages for installation or upgrade.

The following packages have unresolvable dependancies. Make sure that all required repositories are added and enabled in the preferences.

wine:
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed



Btw, when setting Software sources, I realized at the 3rd party tab, that there was this 'WineHQ - Ubuntu 8.04 "Hardy Heron", which I find REALLY odd, since I'm totally sure I downloaded Wine for 7.10.
I'm gonna re-download now.

---

### Post by Rumel on 2008-08-18
You got the error when you sudo apt-get installed because you still had synaptic opened. You have to close synaptic and add/remove to install stuff from command line.

---

### Post by Uner on 2008-08-18
Updated to Ubuntu 8.04, and installed wine without problems.

Thanks alot guys.

---

### Post by becca099 on 2008-09-07
> **Uner said:**
> Updated to Ubuntu 8.04, and installed wine without problems.

Thanks alot guys.
Hello im using Xandros Linux And i get the same error

help me

---

