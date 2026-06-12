---
title: "HPLIP-2.8.7.tar.gz problem??"
date: 2008-08-17
forum: Hardware
---

### Post by Len Tyree on 2008-08-17
I have tried to download hplip-2.8.7.tar.gz and also hplip-2.8.7.run from 'sourceforge.net', they download ok (or so the download folder shows) but they will not archive.  Am unable to load them through 'snaptic' or apt-get??  Any syggestions please?
Thanks, Len Tyree.

---

### Post by eggdeng on 2008-08-17
Hplip comes with ubuntu, are you sure you need to install it?

To install the files you have downloaded, for simplicity, move them to your home directory. The .run file is an installer, like an .exe in W*nd*ws. You can run it by typing ```
~/hplip-2.8.7.run
``` in a terminal.
You will be prompted for your password.

Do **either** the above **or** the following.

If you download a tar file, you are installing manually from source. 
Again, from a terminal, extract the file
```
tar -xvzf ~/hplip-2.8.7.tar.gz
```
Then move into the new folder
```
cd hplip-2.8.7
```
Run 
```
hplip-install
```

---

### Post by Len Tyree on 2008-08-23
SOLVED.
Thanks to eggdeng.

Len Tyree.[http://ubuntuforums.org/images/icons/icon7.gif](http://ubuntuforums.org/images/icons/icon7.gif)

---

