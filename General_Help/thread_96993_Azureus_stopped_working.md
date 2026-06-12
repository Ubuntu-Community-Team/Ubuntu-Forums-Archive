---
title: "Azureus stopped working?"
date: 2005-11-30
forum: General Help
---

### Post by ianpeters on 2005-11-30
Hi!

I recently upgraded to Breezy and since then Azureus has stopped working. I tried a HOWTO that was here in the forums but it didn't help.
The symptom is this; the Azureus splash-screen loads and the loading-meter moves about 1cm and then it just sits there. I tried starting it from xterm but there was no hint of what is wrong.

Does anyone know what can be done?

---

### Post by kairu0 on 2005-11-30
Maybe your installation is using the wrong java.

Try this:

sudo update-alternatives --config java

---

### Post by Gorgonzola on 2005-12-08
I have this exact same problem.

i tried uninstalling Azureus at one point but I can now no longer reinstall it. I now get the following error:
```
gorgonzola@Ubuntu:/usr/bin$ sudo apt-get install azureus
Reading package lists... Done
Building dependency tree... Done
Package azureus is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package azureus has no installation candidate
```

I ran this command:
```
sudo update-alternatives --config java
```
as you suggested and switched it from this:
```
/usr/lib/jvm/java-gcj/bin/java
```
to this:
```
/usr/lib/j2re1.5-sun/bin/java
```

I still have the slight (well, major) problem of not actually being able to reinstall Azureus to see if it will now work.

In case it is relevant, my sources.list looks like this:
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

Any advice will be appreciated!

---

### Post by ianpeters on 2005-12-11
[QUOTE=kairu0]Maybe your installation is using the wrong java.

Try this:

sudo update-alternatives --config java[/QUOTE]

Haha! You were right my friend. For some reason the Breezy upgrade switched to another java as default. Don't ask me why, maybe this should be flagged as a bug? I certainly don't remember a box/dialogue/prompt wanting me to select a java client.

Anyway, thanks a bunch! Hopes this is a help for others as well. Cheers!

---

