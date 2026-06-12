---
title: "Newbie question opening bin files"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by ubtguitarist on 2009-08-03
I am currently trying to install openbravo pos but have run into a bit of trouble. The installaion guide is a bit vague about how to uncompress the bin file to run the installer for an ubuntu command prompt newbie like me. I just dont the commands yet. the name of the file is openbravopos-2.30-linux-installer.bin and it is located on my desktop. how would i go about finding it in terminal and installing it. The installation process is supposed to be pretty easy its just getting to it that stumps me.

Thanks:popcorn:

---

### Post by lisati on 2009-08-03
I'm assuming that you downloaded the file to your desktop.
From the terminal, type in the following (copy and paste should work):
```

cd Desktop
chmod +X openbravopos-2.30-linux-installer.bin
./openbravopos-2.30-linux-installer.bin

```

---

### Post by ubtguitarist on 2009-08-03
I tried what you suggested but i'm getting an error
> 
~/Desktop$ ./openbravopos-2.30-linux-installer.bin
bash: ./openbravopos-2.30-linux-installer.bin: Permission denied

maybe you could help me out interpreting the install guide?

> **Download and install Openbravo POS **


The installers are very simple to follow and the binary package just needs to be opened with your favourite uncompressor and extract all files to an empty folder. 

**  Run it! **

 The first time Openbravo POS starts and there isn't a database, it display a warning alerting that it has found an empty database. If you click OK, Openbravo POS will create for you the database structure necessary to run. 
 ** **

**  On Linux **

 **  Installer **

 In Gnome go to Applications -> Office -> Openbravo POS or just execute  *openbravopos* command in a command line. 
 **  Binary Package **

 Execute *sh start.sh*. 
In linux you first need to add execution permissions to the files *start.sh* and *configure.sh* to do this execute the following commands: 
 chmod +x start.sh 
chmod +x configure.sh 

Thanks in advance if you guys can help me, as i am a complete ubuntu noob

---

### Post by ubtguitarist on 2009-08-04
bump

---

