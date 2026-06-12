---
title: "Where are the downloaded install packages"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by balajist on 2009-08-30
Hi,
Today morning i've downloaded a huge list of applications on ubuntu 9 using Add/Remove packages and am wondering where the .DEB files or the other support files are residing in my hard disk. so that i don't need to download each time when i install ubuntu 9. 
If the .deb files are not in hard disk can we use the installed files (i don't know either where these files are stored) can be back up for installing later. ?

Please help me with this, this will save me enormous amount of time when there is a need to reinstall ubuntu and also when im off line.
Thanks.

---

### Post by oldos2er on 2009-08-30
/var/cache/apt/archives

---

### Post by balajist on 2009-08-30
So  i  need to take a backup of those files and whenever i reinstall ubuntu(9) i need put the files back into the same place or just i can install it right away  ? Sorry am a noob.

---

### Post by oldos2er on 2009-08-30
> **balajist said:**
> So  i  need to take a backup of those files and whenever i reinstall ubuntu(9) i need put the files back into the same place or just i can install it right away  ? Sorry am a noob.

 You can copy the *deb files back to /var/cache/apt/archives and run **sudo dpkg -i /var/cache/apt/archives/*deb**, or run **sudo dpkg -i *deb** from within your backup directory (wherever that may be). It's up to you which way you prefer.

---

### Post by colau on 2009-08-30
Is there any command with apt-get or aptitude to delete those .deb packages from there?

---

### Post by shredder12 on 2009-08-31
Yes,
```
sudo apt-get clean
```
will clear the local repository i.e. /var/cache/apt/archives/.

---

### Post by colau on 2009-08-31
> **shredder12 said:**
> Yes,
```
sudo apt-get clean
```
will clear the local repository i.e. /var/cache/apt/archives/.
Is it similar to:
```

sudo aptitude clean

```

---

### Post by shredder12 on 2009-08-31
yes it is..
you can always check the man page for this.

---

### Post by Katalog on 2009-08-31
There is also an option in the Synaptic preferences under the Files tab to have it automatically delete downloaded packages after the installation is complete (also applies to Update Manager, I believe).

---

### Post by colau on 2009-08-31
Thank you.

---

