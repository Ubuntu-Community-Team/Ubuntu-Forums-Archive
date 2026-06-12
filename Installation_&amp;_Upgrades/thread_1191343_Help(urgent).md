---
title: "Help(urgent)"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by GageG on 2009-06-18
I Get this error when even I try to install something on ubuntu:


'Cannot open /media/toshiba_itunesSetup. exe:No Application suitable for automatic istallation is avalible for handling this kind of file.'

I get this whenever I try to install anything what so ever....HELP?!

---

### Post by merlinus on 2009-06-18
System/Administration/Software Sources.  Untick cdrom and anything else that seems untoward.

---

### Post by GageG on 2009-06-18
I went to the Software sources section but I did not find anything labeled 'cdrom' that could be unchecked.

---

### Post by merlinus on 2009-06-18
Open a terminal.

```

gksu nautilus

```Navigate to /media/ and delete the toshiba file.

---

### Post by GageG on 2009-06-18
I removed the toshiba file (it was a flash drive) but I then tried a disc and it did not work. the same error happened.

---

### Post by merlinus on 2009-06-18
Exactly what are you trying to install, and from where?

---

### Post by GageG on 2009-06-18
Well I have Itunes set up on my flash drive, and when i try to open it from the flash drive it gives me that error. The other thing is a computer game from a CD-rom and when ever I try to open its setup option it gives me the error. and I have also tried to install countless other programs and nothing has ever worked.

---

### Post by merlinus on 2009-06-18
Are these windows programs?  You cannot install them on linux.  You might be able to run them in a VM or with wine, a windows emulator.

Linux does not use .exe files.

---

### Post by GageG on 2009-06-18
I dont know if they are or not. How could I obtain a windows emulator?

---

### Post by merlinus on 2009-06-18
Do a google search for wine.  If the installation files have an .exe extension, then they will not run on linux.

---

### Post by GageG on 2009-06-18
They do. The computer with linux doesnt have internet. could I download it on to my internet enabled computer and then transfer it with a flash drive?

---

### Post by merlinus on 2009-06-18
Don't see why not.  Be sure to visit the wine website to make sure it will support the programs you are wanting to install.

Another possibility, depending upon your system resources, is to use VirtualBox.  It is VM software into which you can install windows and any apps you desire.

---

### Post by GageG on 2009-06-18
so another question. when ever I try to unpackage both Virtualbox and Wine i get an error that says 'Error: Dependency is not satisfiable: libc6' for virtual box and 'Error: Dependency is not satisfiable: winbind' for Wine

---

### Post by Hobgoblin on 2009-06-18
> **GageG said:**
> They do. The computer with linux doesnt have internet. 

That's going to make things much more difficult.  Is there no way you can give it internet?

---

### Post by GageG on 2009-06-18
No, or I just dont know how. Im rather technology brain dead. Can I hook it up to my desktop computers internet and disconnect my desktop for the time being?

---

### Post by merlinus on 2009-06-18
Give it a try -- should work.  If you take the time to do some research, you can easily set up a shared Internet connection for your machines.

---

### Post by raymondh on 2009-06-18
Hello gageG,

See this link when you get a internet connection.  You might find some apps for linux which may substitute for your windows applications.  

[https://help.ubuntu.com/9.04/switching/applications-equivalents.html](https://help.ubuntu.com/9.04/switching/applications-equivalents.html)
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software) 

Of course, if you insist on running windows-specific apps, then VB or Wine should help you (as merlin and others have said)

Happy Ubuntu-ing.

---

### Post by Hobgoblin on 2009-06-19
> **GageG said:**
> No, or I just dont know how. Im rather technology brain dead. Can I hook it up to my desktop computers internet and disconnect my desktop for the time being?

That depends on how your desktop is connected.

---

