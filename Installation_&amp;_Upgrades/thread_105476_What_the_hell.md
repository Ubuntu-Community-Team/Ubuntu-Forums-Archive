---
title: "What the hell?"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by ~LoKe on 2005-12-18
I downloaded the Java Package so I can run Frostwire.  I chose the .rpm as opposed to the .bin because typing sudo alien -i package.rpm just seems easier to me.  After the downlaod finishes, I open the directory and look at the file... It's named jre-1_5_0_06-linux-i586-rpm.bin
Did I just get toally owned?  -rpm.bin? ~_~  What do I do with this now...

---

### Post by doitashimashite on 2005-12-18
Just start that .rpm.bin and it will turn itself into an rpm.

---

### Post by ~LoKe on 2005-12-18
Right you are, thanks!

I've executed the rpm now, no errors so I assume it installed correctly.  But...whenever I try to open Limewire or Frostwire, nothing happens.  Would you happen to knwo what's wrong?

---

### Post by doitashimashite on 2005-12-18
No.

But I didn't install it from the .rpm.
Instead, I installed it from the .bin (jre-1_5_0_06-linux-i586.bin).

This was my procedure and it works under Breezy:

[FONT="Courier New"]$ cd browse_to_your_download_folder
$ sh jre-1_5_0_06-linux-i586.bin
$ sudo mkdir /usr/java
$ sudo mv jre1.5.0_06/ /usr/java/
$ sudo chown -R root:root /usr/java/jre1.5.0_06/
$ sudo ln -s /usr/java/jre1.5.0_06/bin/java /usr/bin/java
$ sudo ln -s /usr/java/jre1.5.0_06/bin/java_vm /usr/bin/java_vm
$ sudo gedit /etc/bash.bashrc[/FONT]

append the lines:
[FONT="Courier New"]JAVA_HOME=/usr/java/jre1.5.0_06
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH[/FONT]

To create Moz symlinks:
[FONT="Courier New"]$ sudo ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
$ sudo ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/
$ sudo ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/[/FONT]

After this, don't forget to logout and login again, since you made changes to your /etc/bash.bashrc file.

---

### Post by ~LoKe on 2005-12-18
Guess I'll download the .bin and try that.

Thanks!

---

### Post by ~LoKe on 2005-12-18
Did that, still doesn't work. :(

---

### Post by NotJustANewbie on 2005-12-18
Add these two lines to your /etc/apt/sources.list:
```
deb http://ftp.debian-unofficial.org/debian sarge main contrib non-free restricted
deb-src http://ftp.debian-unofficial.org/debian sarge main contrib non-free restricted
```

do:
```
sudo apt-get update
sudo apt-get install sun-j2se5.0-jre-binary
sudo apt-get install limewire-free-binary
```

There you go, all better now. lol

---

### Post by ~LoKe on 2005-12-18
Huge download for my low-end cable.  But...I'll give it a shot.  Thanks for the help. ;)

---

### Post by noigeaR on 2005-12-18
ubuntu comes pre-installed with a java version that's not very compatible with standalone apps (it's called GIJ i think) and even if you install an alternative java (like sun or blackdown) they will not automatically replace GIJ.
maybe sun java is already installed correctly on your computer, but it might not be the default jvm. from a terminal run ```
sudo update-alternatives --config java
```
if there is more than one java in the list, choose the sun java and it will be used as default from now on.
you can find out if sun java is your default with the followin command in a terminal ```
java -version
```
for sun java this should print something like
> java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

---

### Post by ~LoKe on 2005-12-18
Did both of the suggestions listed and now Frostwire works!

I wub you guys.

---

