---
title: "Syntheic  Package Manager Error"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by msohn88 on 2009-02-27
I tried to install Skype through Terminal, but somehow I messed up my SPM.

E: Type '--2009-02-26' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Solutions?

---

### Post by Elfy on 2009-02-27
There is an error in the file Type '--2009-02-26' is not known on line 1

I would remove the file and start again

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

**If** you want to fix the line then open for editing and don't use the rm command above, otherwise miss this bit and move on to the sudo wget command

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

Each line should start either deb or deb-src - it is likely that the whole file is wrong.

Use this to add the medibuntu list for intrepid from a terminal

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Then add the key

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

If you are not running intrepid get the corresponding line for your version here
[https://help.ubuntu.com/community/Medibuntu#Adding](https://help.ubuntu.com/community/Medibuntu#Adding) the Repositories

---

### Post by msohn88 on 2009-02-27
Do I type first two in the terminal?

I get 

min@min-laptop:~$ sudo rm /etc/apt/sources.list.d/mediubuntu.list
[sudo] password for min: 
rm: cannot remove `/etc/apt/sources.list.d/mediubuntu.list': No such file or directory

---

### Post by Elfy on 2009-02-27
Typing commands out is good as long as you type the right thing - it's medibuntu not mediubuntu :)

If you're not sure then copy and paste

---

