---
title: "[SOLVED] Firefox 3 Problems --need asap help pls!--"
date: 2008-08-19
forum: General Help
---

### Post by unseend on 2008-08-19
Howdy ppl!

I have a 'hawt' problem. Recently I upgraded to Firefox 3. I downloaded the .tar.bz2 package from mozilla's site and followed the instructions from there to upgrade to 3 from 2. I have a problem though. I want to get back to firefox 2.0.0.16!!!

How can I do that? I tried deleting from Synaptic (Remove & Complete Removal), from Add/Remove, with sudo apt-get purge firefox, and after each one I do a sudo apt-get install firefox but it installs again the 3rd version. Furthermore in Synaptics it says in the description of firefox package ver. 2.0.0.16 but it still downloads 3.0.1.

What can I do? Please advice me!

Thanx in advance!

---

### Post by nitro_n2o on 2008-08-19
since you downloaded firefox 3 manually it'll go to /usr/local/bin and if you check your path echo $PATH usually you'll see that /usr/local/bin is before /usr/bin, you'll get something like this /usr/local/bin:/usr/bin 
meaning that linux will search for executables in /usr/local/bin before searching in /usr/bin .. but i'm sure that you have firefox2 in /usr/bin 

just type this ./usr/bin/firefox and see if that gives you firefox2 

to make this permanent change the symlink in /usr/local/bin/firefox to /usr/bin/firefox 

sudo ln -s /usr/bin/firefox /usr/local/bin/firefox 
or change the command in the panel launcher to /usr/bin/firefox %u

good luck

---

### Post by unseend on 2008-08-19
> **nitro_n2o said:**
> since you downloaded firefox 3 manually it'll go to /usr/local/bin and if you check your path echo $PATH usually you'll see that /usr/local/bin is before /usr/bin, you'll get something like this /usr/local/bin:/usr/bin 
meaning that linux will search for executables in /usr/local/bin before searching in /usr/bin .. but i'm sure that you have firefox2 in /usr/bin 

just type this ./usr/bin/firefox and see if that gives you firefox2 

to make this permanent change the symlink in /usr/local/bin/firefox to /usr/bin/firefox 

sudo ln -s /usr/bin/firefox /usr/local/bin/firefox 
or change the command in the panel launcher to /usr/bin/firefox %u

good luck

1) if I type ```
./usr/bin/firefox
``` I get ```
apas@apas:~$ ./usr/bin/firefox
bash: ./usr/bin/firefox: No such file or directory
```

2) if I type ```
/usr/local/bin/firefox
``` I get ```
apas@apas:~$ /usr/local/bin/firefox
bash: /usr/local/bin/firefox: No such file or directory

```

3) firefox %u gets me to Firefox 3.

---

### Post by gjoellee on 2008-08-19
you have firefox installed and it should be seen in synaptic. You may remove firefox 3 from synaptic and install 2.0.0.16

---

### Post by unseend on 2008-08-19
> **gjoellee said:**
> you have firefox installed and it should be seen in synaptic. You may remove firefox 3 from synaptic and install 2.0.0.16

I said I can't because in synaptic it says about firefox 2.0.0.16 version in description of the 'firefox' package but it's NOT! (soz caps) It downloads me still the 3.0.1 version!

And from synaptic if I search for 'firefox' i don't see any Firefox 3 package except from one that it's beta. Before FF 3 normal version was released. 

**The only thing from Windows I like is the easy install/uninstall :-)**

---

### Post by aysiu on 2008-08-19
You have to explain to us by what method you "installed" the .tar.bz2 Firefox 3.

If you explain how you installed it, we can help you remove it.

---

### Post by mb_webguy on 2008-08-19
Firefox 3 won't show up in Synaptic if he didn't install it from a deb package.

If you installed FF3 using the "./configure; make; sudo make install" route, then you should be able to uninstall it by going to the directory where you unpacked the source code -- download and upack it again if necessary -- and typing "./configure; make; sudo make uninstall".

---

### Post by aysiu on 2008-08-19
> **mb_webguy said:**
> Firefox 3 won't show up in Synaptic if he didn't install it from a deb package.

If you installed FF3 using the "./configure; make; sudo make install" route, then you should be able to uninstall it by going to the directory where you unpacked the source code -- download and upack it again if necessary -- and typing "./configure; make; sudo make uninstall".
The normal .tar.bz2 download from Mozilla is a precompiled binary, not source code.

---

### Post by unseend on 2008-08-19
> **aysiu said:**
> You have to explain to us by what method you "installed" the .tar.bz2 Firefox 3.

If you explain how you installed it, we can help you remove it.

doing what [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) in the manual install section says. It is a link reference how to install new firefox realeases from mozilla.

---

### Post by gjoellee on 2008-08-19
> **unseend said:**
> I said I can't because in synaptic it says about firefox 2.0.0.16 version in description of the 'firefox' package but it's NOT! (soz caps) It downloads me still the 3.0.1 version!

so sorry didn't catch that :KS

---

### Post by aysiu on 2008-08-19
> **unseend said:**
> doing what [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) in the manual install section says. It is a link reference how to install new firefox realeases from mozilla.
Paste these commands in the terminal, and you should be fine, then: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
mv ~/.mozilla ~/.mozilla.manual.download
mv ~/.mozilla.backup ~/.mozilla
sudo rm -r /opt/firefox
``` That's from [the removing section of the same page you got the installation instructions from](https://help.ubuntu.com/community/FirefoxNewVersion#Removing).

---

### Post by unseend on 2008-08-19
> **gjoellee said:**
> so sorry didn't catch that :KS


it says that it's the 2.0.0.16 version but downloads the 3.0.1!!!!! :P

---

### Post by unseend on 2008-08-19
guys thanx for trying to help me but hopefully and at last I am back with my beloved 2.0.0.16 FF version!!!

How I did it?
Downloaded the 2.0.0.16 package from mozilla.com
Complete Remove of Firefox from Synaptic
entered cd /home/apas/firefox
./firefox
then back to synaptics and installed the firefox package

thanx all of you for trying to help me! :-D :-D:D:D:D:D:D

---

