---
title: "synaptic package manager failure?"
date: 2008-07-23
forum: General Help
---

### Post by janosp on 2008-07-23
I am getting the following error message:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/Xubuntu%208.04.1%20%5fHardy%20Heron%5f%20-%20Release%20i386%20(20080702.1)_dists_hardy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

searching for the error messages, various solutions were suggested, but none seemed to work. Being a n00b, I a flummoxed.

What does the error message mean? And what do I do about it?

I am trying to resuscitate an old Dell Latitude for my parents to use...

Any suggestions would be really appreciated!

---

### Post by iaculallad on 2008-07-23
Create a backup of the original status file:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.original
```

and, replace it with the -old status file:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then redo your package management.

---

### Post by janosp on 2008-07-24
Thanks, I'll try it. 
But what do you mean by 'redo your package management' (n00b alert...)
j

---

### Post by iaculallad on 2008-07-24
> **janosp said:**
> Thanks, I'll try it. 
But what do you mean by 'redo your package management' (n00b alert...)
j

What that phrase means is for you to continue installing the application or updates that had caused that error message.

---

### Post by janosp on 2008-07-24
Did as suggested. Unfortunately when I tried to run Synaptic, I still got:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/Xubuntu%208.04.1%20%5fHardy%20Heron%5f%20-%20Release%20i386%20(20080702.1)_dists_hardy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

The error msg at the top of the box said 'could not initialize the package information'

Any thoughts?

---

### Post by iaculallad on 2008-07-24
Close all opened Synaptics or Add/Remove window and open your terminal.

```
sudo dpkg --configure -a
sudo apt-get update & sudo apt-get upgrade
```

---

### Post by janosp on 2008-07-24
Rats.. still giving same error!
j

---

### Post by iaculallad on 2008-07-24
This would be our last option/solution for that: On your terminal, issue the commands below:

```
sudo rm /var/lib/apt/lists/Xubuntu%208.04.1%20%5fHardy%20Heron%5f%20-%20Release%20i386%20(20080702.1)_dists_hardy_main_ binary-i386_Packages

```

then

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by janosp on 2008-07-24
copied and pasted and got an error:

sudo rm /var/lib/apt/lists/Xubuntu%208.04.1%20%5fHardy%20Heron%5f%20-%20Release%20i386%20(20080702.1)_dists_hardy_main_ binary-i386_Packages
bash: syntax error near unexpected token '('

This is a new install of Xubuntu. The only thing I did was to install a Marvel wireless driver to run a Netgear card, following instructions here on the forums. It works fine.

J

---

### Post by iaculallad on 2008-07-24
Again, on your terminal, Try this instead:

```
sudo cp -R /var/lib/apt/lists /var/lib/apt/lists.backup
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by janosp on 2008-07-24
Thanks! I think the problem is solved. Synaptic is now downloading updates, no error msgs thus far!
Again, thanks for your help!!!
J

---

