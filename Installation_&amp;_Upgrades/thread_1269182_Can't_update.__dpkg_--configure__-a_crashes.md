---
title: "Can't update.  dpkg --configure  -a crashes"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by jsegel on 2009-09-17
On a laptop, 9.04
Can't run apt-get anything, without getting an error saying dpkg interrupted,
sudo dpkg --configure -a

Doing so freezes the computer. 

can't uninstall what's wrong, can't install anything, can't update anything. :confused:

---

### Post by wojox on 2009-09-17
Try:

```
sudo apt-get -f install
```

Followed by:

```
sudo dpkg --configure -a
```

---

### Post by jsegel on 2009-09-18
well, like i said:

> **wojox said:**
> Try:

```
sudo apt-get -f install
```

Followed by:

```
sudo dpkg --configure -a
```

sudo apt-get -f install   
 fails, 
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."


sudo dpkg --configure -a

Setting up mono-gac (2.0.1-4ubuntu0.1) ...
* Installing 1 assembly from libgnome-keyring1.0-cil into Mono


results in a dead computer.  mouse works, trying to run anything else gives endless spinning.

---

### Post by bumanie on 2009-09-18
Could try > sudo apt-get update && sudo apt-get upgrade

---

### Post by jsegel on 2009-09-18
apt-get update or upgrade produce the same result.
apt-get    anything at all won't finish, Errors about dpkg. same.

---

### Post by bumanie on 2009-09-18
You may have to purge the broken package and then try to download it again. > sudo aptitude purge <name of package>This should get rid of the errant package and its config file.

---

### Post by jsegel on 2009-09-18
> **bumanie said:**
> You may have to purge the broken package and then try to download it again. This should get rid of the errant package and its config file.

thanks for the suggestion, but this produces the same error. (dpkg was interrupted, etc)

btw i was trying to purge mono, but any aptitude command produces the same result.

---

### Post by jsegel on 2009-09-19
:KS
I believe this problem is over,
I installed dselect and used that in favor of dpkg
sudo dselect 
choosing config  and all
somehow this took care of the config of packages that running dpkg --configure -a   would cause the computer to crash.
fingers crossed but it appears that apt-get update works, apt-get upgrade is also working.

---

### Post by jsegel on 2009-09-19
agh, spoke too soon, it's hung on:
```
* Installing 1 assembly from libgnome-keyring1.0-cil into MONO
```


should i assume that somehow it's MONO that's screwed up?:(

---

### Post by jsegel on 2009-09-19
many tries to make it through:

```
sudo apt-get remove --purge mono-runtime mono-common libmono0
```

results in
```
 sudo apt-get update 
sudo apt-get upgrade

```

running smoothly and completing.


Mono "provides the necessary software to develop and run .NET client and server applications on Linux, Solaris, Mac OS X, Windows, and Unix."


why is it in Ubuntu to begin with?


look here for alternatives to Mono-based apps:
[http://www.theopensourcerer.com/2008/08/04/how-to-remove-mono-m-from-ubuntu-hardy-heron/](http://www.theopensourcerer.com/2008/08/04/how-to-remove-mono-m-from-ubuntu-hardy-heron/)
:popcorn:

---

### Post by directhex on 2009-09-19
> **jsegel said:**
> why is it in Ubuntu to begin with?

Because the desktop team want F-Spot and Tomboy, which happen to be written in C#

---

### Post by polarberg on 2009-10-19
Hi. Just installed ubuntu-studio and am having the same problem. Package manager hung and I had to force shutdown, thus leaving a bunch of broken packages, and dpkg --configure -a hangs on openoffice.org-emailmerge. Escaping causes it to hang on atomix-data, which i then can't escape out of.

I've tried every suggestion in this thread to no avail. Running "Repair broken packages" in recovery mode as suggested [here]("http://ubuntuforums.org/archive/index.php/t-1288763.html") __runs dpkg with the last line "Fixing recursive fault but reboot is needed!" There are a couple "can't remove ... : no such file or directory" errors at the beginning of dpkg's output (in recovery mode) but I can't catch what they refer to.

My level of experience is pretty low - I tried Linux once when I was a kid but it was years ago; this install is a few days old.

(The moral seems to be: Don't install too many packages at once.)

---

### Post by polarberg on 2009-10-19
Well, solved, kinda. In case this happens to anyone else:

dpkg -r <package>

which in my case was openoffice.org-emailmerge. Same thing apparently happened to [this]("http://ubuntuforums.org/archive/index.php/t-1234869.html") person, and openoffice appears to cause problems with ubuntu-studio. This worked fine for me, but it's hanging again on ca-certificates-java, which I couldn't remove due to dependency issues. So I ran:

apt-get purge ca-certificates-java

which gave me a daunting list of packages which would be removed but nothing's broken yet. Hopefully I didn't just give ubuntu a heart attack.

---

