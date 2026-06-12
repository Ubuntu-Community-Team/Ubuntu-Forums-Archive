---
title: "Partial Upgrade warning persistent after upgrade to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by rockfx01 on 2009-04-24
After performing the upgrade from 8.10 to 9.04, whenever I open update manager I receive a warning stating "Not all updates can be installed."

If I click [Close], I see "liblucene2-java" greyed out in the Distribution updates list.

If I click [Partial Update], it tries to do an upgrade.  In the upgrade list it wants to change the following packages:
[INDENT]Remove libdb4.5-java
Install libdb4.6-java
Install libdb4.6-java-gcj
Upgrade liblucene2-java[/INDENT]

I click [Start Upgrade] and the upgrade seems to fail - the upgrade window closes at some point and no final confirmation is ever displayed saying the installation completed successfully.

The "Not all updates" warning keeps popping up because the upgrade does not succeed.

---

### Post by toontastic on 2009-04-24
> **rockfx01 said:**
> After performing the upgrade from 8.10 to 9.04, whenever I open update manager I receive a warning stating "Not all updates can be installed."

If I click [Close], I see "liblucene2-java" greyed out in the Distribution updates list.

If I click [Partial Update], it tries to do an upgrade.  In the upgrade list it wants to change the following packages:
[INDENT]Remove libdb4.5-java
Install libdb4.6-java
Install libdb4.6-java-gcj
Upgrade liblucene2-java[/INDENT]

I click [Start Upgrade] and the upgrade seems to fail - the upgrade window closes at some point and no final confirmation is ever displayed saying the installation completed successfully.

The "Not all updates" warning keeps popping up because the upgrade does not succeed.

Can't help I'm afraid but I'm having the exact same problem with the same packages actually so any help gratefully received.

---

### Post by toontastic on 2009-04-24
Actually going into terminal and typing 

 sudo apt-get update && sudo apt-get dist-upgrade

Seems to fix this.

---

### Post by rockfx01 on 2009-04-24
Yep, that worked, thanks!

Must be something wrong with the graphical partial updater.

---

### Post by freakyhash on 2009-04-25
thanks worked for me too....

---

### Post by Lachinchon on 2009-04-25
Toontastic, you da man!  Worked for me, too.

---

### Post by bigger.tigger on 2009-04-26
I experienced this issue too.

It appears that the upgrade manager was confused because I had already upgraded to Java 6 on my old (Intrepid) distro. Java 6 isn't part of the standard build, so it's not too surprising that Ubuntu reported an error.

The 'sudo apt-get...' worked for me too - thanks for the fix.

---

### Post by MikeB007 on 2009-04-26
I've had a similar experience however I get the following error:

Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg-query: parse error, in file `/var/lib/dpkg/available' near line 39536 package `libisccfg30':
 field name `
exim4-config.postinst: [WARN] Installed debconf version is broken. Aborting preconfigure.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 39536 package `libisccfg30':
 field name `
dpkg: parse error, in file `/var/lib/dpkg/available' near line 39536 package `libisccfg30':
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

Any ideas from anyone would be appreciated.  Cheers.

---

### Post by dewbuntu on 2009-04-26
This worked for me too!  Ran the upgrade to 9.04 last night and this morning I was getting the exact same error with the partial upgrade warning.  

BTW, other than this minor issue, everything is working great, have not found any issues with installed applications.

D

---

### Post by dfrado on 2009-04-26
Thanks for the solution toontastic!  Much appreciated! :)

---

### Post by MikeB007 on 2009-04-26
From my last post it seemed the file was corrupted.  So:  

[INDENT]
[LIST=1]
[*]ran 'sudo dpkg --configure -a' which cleared the 'available' file;
[*]ran 'sudo aptitude dist-upgrade'
[/LIST]
[/INDENT]
The upgrade proceeded as expected ... well longer than I expected but I have several third party apps so ....  HTH

---

### Post by ComputerExpertVK on 2009-04-26
Thank you!
This helped a lot!

---

### Post by BlueZED on 2009-04-27
Hi there,

I had the same problem but unfortunately none of the solutions here worked for me.
So I did some digging and when I tried to Fix broken Packages in Synaptic I got this error:
```
dpkg: error processing /var/cache/apt/archives/libsox-fmt-base_14.2.0-1_i386.deb (--unpack): 
trying to overwrite `/usr/lib/sox/libsox_fmt_sndfile.so', which is also in package 
libsox-fmt-sndfile
```I then manually removed libsox_fmt_sndfile.so using
```
sudo dpkg -r libsox_fmt_sndfile.so
```That solved it for me.

Hope it helps someone else too.

---

### Post by Digital Magi on 2009-04-29
> **toontastic said:**
> Actually going into terminal and typing 

 sudo apt-get update && sudo apt-get dist-upgrade

Seems to fix this.
Thanks for the help, your advice was just the thinkg to fix my install.

---

### Post by wimpelmeesje on 2009-05-03
toontastic's fix worked for me, thanks!

---

### Post by 3mpy on 2009-05-12
Nice! Thank yo very much!

---

