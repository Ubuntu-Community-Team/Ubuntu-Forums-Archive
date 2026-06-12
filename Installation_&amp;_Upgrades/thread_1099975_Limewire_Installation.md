---
title: "Limewire Installation"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by nickyn on 2009-03-18
I've downloaded Limewire for Linux, and got it mostly installed until the last little bit, then I get this error message:
```
Could not open 'LimeWireLinux.deb'
The package might be corrupted or you are not allowed to open the file.  Check permissions of the file.
```

And in the terminal installation thing, it says:
```
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: error processing /tmp/LimeWireLinux.deb (--install):
 cannot access archive: No such file or directory
```

Can anyone help?

---

### Post by Partyboi2 on 2009-03-18
Download a frresh copy of the limewire deb, then double click on it to install it. Or you could try  [[COLOR=Blue]frostwire[/COLOR]]("https://help.ubuntu.com/community/FrostWire")

---

### Post by nickyn on 2009-03-19
Thanks, I downloaded FrostWire, and that installed no problem!

---

### Post by doomsmith on 2009-03-24
I downloaded Frostwire and installed it with no problems.  but I go to start it and nothing happens.  What do I do to fix this problem?

---

### Post by KCG102282 on 2009-03-24
Open it up in a terminal and see what pops up, but from my exoerience you probably don't have Java installed so you need to install it.

---

### Post by meho_r on 2009-03-24
Start it from a terminal and check out what the error is. It is probably java issue.

EDIT: try with```
sudo update-alternatives --config java
```

It will list all java installed (in case more than one exists). Select one and try again. If still FrostWire doesn't work, try with other one. Sun java should work though.

---

### Post by bigtom2 on 2009-03-24
when you install limewire you must open details tab it askes
if you want to install java you just go down to bottom
of the disclaimer an type yes.

it will install good have fun bigtom.

---

### Post by doomsmith on 2009-03-24
This is what happened when I opened it in a terminal:

file:///home/doomsmith/Desktop/Screenshot-doomsmith%40Doom%3A%20~.png

Then this is what happened when I ran a check for Java:

file:///home/doomsmith/Desktop/Screenshot-doomsmith%40Doom%3A%20~-1.png

What next?

---

### Post by doomsmith on 2009-03-24
I'm sorry those screen shots didn't show in my posts.  But the firs was: Found no such file or directory/

And the other was:

"There is only 1 program which provides Java (/usr/bin/gij-0wrapper-4.1). Nothing to configure"

What do I do next?

---

### Post by doomsmith on 2009-03-25
Can somebody please help me?

---

### Post by meho_r on 2009-03-25
Well, try installing sun java for starters. Do a search in Synaptic. You should find something like sun-java6-jre and ia32-sun-java6.

Alternatively, you can install openjdk java if you don't want sun's version (packages openjdk-6-jre and icedtea6-plugin I think). I have both versions installed and switch them if necessary with sudo update-alternatives --config java (some programs still won't work with openjdk, especially if you're using 64bit ubuntu).

---

### Post by hubcity on 2009-03-28
link... it helped me get frostwire up and running...

[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

hope it helps...

jim

---

### Post by rvec on 2009-05-18
> **nickyn said:**
> Thanks, I downloaded FrostWire, and that installed no problem!

same here....I downloaded FrostWire 4.18.0, and it installed no problem on Ubuntu 9.04 (64bit)!

Looks exactly like the Limewire version.

Thanks

---

