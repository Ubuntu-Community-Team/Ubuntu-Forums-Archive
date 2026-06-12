---
title: "please help with running mindstorms nxt"
date: 2008-11-08
forum: General Help
---

### Post by midododo11 on 2008-11-08
hi 
i have ubuntu and i dont know how to run mindstorms nxt program
on it please help and i tried with wine also but it doesnt work :confused:
i dont want to return to windows again:(
and thanks

---

### Post by Nepherte on 2008-11-08
You certainly don't need windows to use nxj mindstorms. Just download the correct package: [http://lejos.sourceforge.net/nxj-downloads.php](http://lejos.sourceforge.net/nxj-downloads.php) and extract it to, let's say /opt/lejos_nxj for example. There's no need to 'install' anything, extracting will do. Afterwards you'll need to set up the necessary environment variables. These are the ones I have:
```
export NXJ_HOME=/opt/lejos_nxj
export PATH=$PATH:$NXJ_HOME/bin
export JAVA_HOME=/path/to/java
```
You can add them to .bashrc so they are set every time you login (you will need to relogin the first time to have them working). Note that you will also need the variable JAVA_HOME pointing to your java directory, but you might already have that one (remember to replace /path/to/java to the actual path). You can see if a variable (for example NXJ_HOME) has been set with:
```
echo $NXJ_HOME
```

From then on, you can use the command line to compile, link, upload & run nxj programs with respectively nxjc, nxjlink, nxjupload. Another way is to use an integrated development environment such as eclipse + ant to build your programs. For a full explanation about nxj, see their website: [http://lejos.sourceforge.net/nxt/nxj/tutorial/index.htm](http://lejos.sourceforge.net/nxt/nxj/tutorial/index.htm)

---

