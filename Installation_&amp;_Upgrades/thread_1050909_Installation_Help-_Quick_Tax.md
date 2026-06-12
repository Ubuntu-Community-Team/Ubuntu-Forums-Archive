---
title: "Installation Help- Quick Tax"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by schmengei on 2009-01-26
How is this done with Ubuntu?
How to activate the setup.exe?
I'm a complete novice on installation procedures with this system. Thanks in advance, Peter.

---

### Post by overlord.gaurav on 2009-01-26
To learn on how to install softwares on Ubuntu go [here.]("http://www.psychocats.net/ubuntu/installingsoftware")

Also, you can't really install executable [.exe] files on Ubuntu. Although you can install Wine [windows emulator] to run .exe files on Ubuntu. But, wine will NOT run all of your programs. To install wine click on Applications > Accessories > Terminal > And paste this :

```
 sudo apt-get install wine 
```
Enter your password. Once wine is installed you can try running your files. But there are more chances of the file note working.

---

### Post by schmengei on 2009-01-31
Thanks overlord.

---

### Post by CiaoCiao on 2009-03-27
I don't know if Quick Tax will work or not but I can confirm that future tax does work under wine.

[http://ubuntuforums.org/showthread.php?p=6898713#post6898713](http://ubuntuforums.org/showthread.php?p=6898713#post6898713)

---

### Post by Mark Phelps on 2009-03-29
CodeWeavers (the producers of Wine) keep a database of application compatibility -- because not all Windows apps work on Wine, and those that do, have varying degrees of success.

Below is the link to the page for Quick Tax.  It has a silver rating which means it has some problems:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4446]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=4446")

---

