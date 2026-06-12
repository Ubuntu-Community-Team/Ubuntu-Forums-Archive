---
title: "[SOLVED] How can I find what a .deb depends on?"
date: 2008-09-09
forum: General Help
---

### Post by dodle on 2008-09-09
I would like to be able to see what one of my .deb packages depends on.  All dependencies are met, but I would like to know what those dependencies are.  Is there a way to do this?

---

### Post by stoneage on 2008-09-09
System => Administration => Synaptic Package Manager

Right click on the package and choose Preferences

Or check [http://packages.ubuntu.com](http://packages.ubuntu.com) for a comprehensive listing

---

### Post by dodle on 2008-09-09
Actually, the package isn't in the repositories.  I have the .deb downloaded to my computer.

---

### Post by stoneage on 2008-09-09
Ah, umm, you could try installing it...

Seriously though, does it have a homepage, it should be listed there.

---

### Post by dodle on 2008-09-09
Good point, I'll try installing it.  The homepage does show some dependencies, but I would like to know which versions.

---

### Post by dodle on 2008-09-09
Awwww, "poperties" in synaptic doesn't show any dependencies.  I had to convert it from an .rpm to a .deb using alien.  I don't like the meta info that alien puts in, so I'm repackaging it but want to list the dependencies.

Is there any way to check dependencies of an .rpm package?

---

### Post by stoneage on 2008-09-09
There is a thread here that maybe you could adapt, but you would, I think, have to be able to install with Synaptic:-

[http://ubuntuforums.org/showthread.php?t=501236](http://ubuntuforums.org/showthread.php?t=501236)

---

### Post by Titan8990 on 2008-09-09
what program is this?

---

### Post by Vivaldi Gloria on 2008-09-09
dodle, use

```
dpkg -I file.deb
```

---

### Post by dodle on 2008-09-09
[QUOTE=Titan8990]what program is this? [/QUOTE]
It's Mahjongg3d, I am making a .deb package for it.
[QUOTE=Vivaldi Gloria]```
dpkg -I file.deb
```[/QUOTE]
```
~/Desktop$ sudo dpkg -i mahjongg3d_0.96-1_i386.deb
(Reading database ... 145693 files and directories currently installed.)
Preparing to replace mahjongg3d 0.96-1 (using mahjongg3d_0.96-1_i386.deb) ...
Unpacking replacement mahjongg3d ...
Setting up mahjongg3d (0.96-1) ...

```
alien deletes the dependency information when it creates the .deb file for some reasean.  Might it keep it if I did this:```
sudo alien -c mahjongg3d-0.96-SuSE_91.i586.rpm
```

What tool can I use to extract an rpm package?

---

### Post by Vivaldi Gloria on 2008-09-09
Something like

```
rpm --query -i foo.rpm
```

should give package info including dependencies. See

```
man rpm
```


> **dodle said:**
> Might it keep it if I did this:```
sudo alien -c 

Don't know. Try.

> What tool can I use to extract an rpm package?

Alien might do that. See 

[CODE]man alien
```

to find the option.

---

### Post by dodle on 2008-09-09
> **dodle said:**
> ```
sudo alien -c mahjongg3d-0.96-SuSE_91.i586.rpm
```

Sweet!  This worked.  Actually I did:```
sudo alien -cv mahjongg3d-0.96-SuSE_91.i586.rpm
```Apparently by telling alien to keep the scripts (-c) transfers all dependency information over to the .deb.  Thanks for your help everyone, and i recommend using the -c parameter whenever making a .deb from an .rpm with alien.

---

### Post by dodle on 2008-09-09
Does anyone want this deb package?  I guess I should have checked to see if the game was any good before I went to all of this trouble.

---

### Post by stoneage on 2008-09-09
PS - > **dodle said:**
> If time is a line, What point am I at? <_____.__>


You're not at a point, you are smeared all across the line with probability weightings for certain states.

---

