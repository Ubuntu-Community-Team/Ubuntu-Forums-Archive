---
title: "What is your favorite FTP program for Linux?"
date: 2008-07-10
forum: General Help
---

### Post by hotpinkflamingo on 2008-07-10
Hi all,
I'm a semi-recent convert from Windows.  I used to use WSFTP pro.  Since I've switched to Ubuntu, I've just been using the gFTP program that came with it, but I don't like it much.  Are there any Linux FTP programs that are more full featured like WSFTP?  What are some good ones I should check out?  I'd prefer one with a GUI as opposed to command line.

---

### Post by BUSHYBOB on 2008-07-10
I'm using Filezilla.

---

### Post by Pablo89 on 2008-07-10
gFTP is just the simplest and nicest one for me. And, while FileZilla is in universe, gFTP is in main :)... what exactly don't you like about that program? I've never noticed lack of any features...

---

### Post by hotpinkflamingo on 2008-07-10
> **Pablo89 said:**
> And, while FileZilla is in universe, gFTP is in main

I'm not sure what you mean by that?
Well, gFTP doesn't have a pause function for one.  I just don't like the controls; everything is awkward and takes too many steps....

---

### Post by cpetercarter on 2008-07-10
I like the FireFTP extension for Firefox.

---

### Post by jimv on 2008-07-10
As far as features go, FileZilla FTW.

Also, you can get CurlFTPFS and mount an FTP server on a folder and use it like it was a local drive.

---

### Post by nikgare on 2008-07-10
You could always use Nautilus

---

### Post by ibutho on 2008-07-10
I'm a recent convert to FileZilla although gFTP served me well for many years.

---

### Post by MasterXandrex on 2008-07-10
> **hotpinkflamingo said:**
> I'm not sure what you mean by that?


He means the repositories. If something is in main you can get it by default bu typing 

```

sudo apt-get install thing

```

if it's in universe (I think) or multiverse you have to enable those repos in your APT sources.

Xan

BTW, I use nautilus of the command line... and recently sshfs.

---

### Post by djxcon on 2008-07-10
I would say a combination of FireFTP (Firefox Extension) and GFTP.  FileZilla has come a long way in Linux though so really, all three are great  Wow, I'm no help! :)

---

### Post by hotpinkflamingo on 2008-08-14
Thanks for the suggestions.  I want to try out FileZilla.  When I find it using synaptic, the version in there is 3.0.7.1, but on the FZ web site the latest version for Linux is 3.1.1.1.  On their site it states for Linux "It is recommended to use the package management system of your distribution or to manually compile FileZilla instead."

Does anyone know how I can install the latest version, and why it doesn't show up in synaptic?

---

### Post by decoherence on 2008-08-14
> **hotpinkflamingo said:**
> Does anyone know how I can install the latest version, and why it doesn't show up in synaptic?

The repositories contain versions that are tried and tested to work with Ubuntu so by necessity they are somewhat out of date. 

Every six months everything is updated to the latest version and we get a new release of Ubuntu (there are of course bug fixes and security fixes in the mean time.)

Unless the latest version has features you need, I suggest sticking with the tried and tested if you value your system stability.

That said, there are more recent packages from 3rd party sources including getdeb.net

---

### Post by hotpinkflamingo on 2008-08-14
I see, thanks for explaining.  :)

---

