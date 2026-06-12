---
title: "moving a file into write protected directory"
date: 2008-07-19
forum: General Help
---

### Post by baddison on 2008-07-19
Hi
I'm trying to move the following license file into a directory to make IDL work.  I can't seem to get the syntax right.  I'm logged in as root.
mv "/Desktop/License.dat" "/usr/local/rsi/license/License.dat"
I get the following error:
mv: cannot stat `/Desktop/License.dat': No such file or directory
root@brett-laptop:/usr/local/rsi/license# 
I should be able to move the file since I was able to create folders in this directory.  Any help would be appreciated.
Thanks

---

### Post by audwan on 2008-07-19
If the License-file is on your desktop, try
mv ~/Desktop/License.dat /usr/local/rsi/license/License.dat

---

### Post by Vivaldi Gloria on 2008-07-19
> **baddison said:**
> Hi
I'm trying to move the following license file into a directory to make IDL work.  I can't seem to get the syntax right.  I'm logged in as root.
mv "/Desktop/License.dat" "/usr/local/rsi/license/License.dat"
I get the following error:
mv: cannot stat `/Desktop/License.dat': No such file or directory
root@brett-laptop:/usr/local/rsi/license# 
I should be able to move the file since I was able to create folders in this directory.  Any help would be appreciated.
Thanks

Use this

```
mv /home/<username>/Desktop/License.dat /usr/local/rsi/license/License.dat
```

Replace <username> with your username.

If it's on root's desktop then use this:

```
mv /root/Desktop/License.dat /usr/local/rsi/license/License.dat
```

Don't forget that linux is case sensitive.

Or just press Alt+F2 and start

```
gksudo nautilus
``` 

to get a nautilus window with root rights. You can copy using it.

---

### Post by baju on 2008-07-19
if the file is on your desktop you can simply use
```
~/Desktop/
```
as path.

---

