---
title: "root permission problem"
date: 2008-10-20
forum: General Help
---

### Post by drew boardman on 2008-10-20
Hi

I need to edit sources.list but its owned by root.  I am sole user.  I thought I was in the root group (see below) therefore I could just edit it  and save but the system won't let me.  Any ideas?

drew@drew-desktop:/etc/apt$ id drew
uid=1000(drew) gid=0(root) groups=0(root),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),114(admin)
drew@drew-desktop:/etc/apt$ chmod ug+rw sources.list
chmod: changing permissions of `sources.list': Operation not permitted
drew@drew-desktop:/etc/apt$


Thanks

Drew

---

### Post by /////// on 2008-10-20
use the sudo command to gain temporary root access

---

### Post by Hangwire on 2008-10-20
> **/////// said:**
> use the sudo command to gain temporary root access

Exactly.

```
sudo /etc/apt$ chmod ug+rw sources.list
```

It will ask you for your password, enter it, hit enter and there you go.

---

### Post by drew boardman on 2008-10-20
Dear //// and Hangwire

Thanks for the quick responses.

I did 
"drew@drew-desktop:/etc/apt$ sudo chmod ug+rw sources.list
drew@drew-desktop:/etc/apt$"

Went back to Dolphin, opened the file, removed the offending line, tried to save and error, don't have permission!

Drew

---

### Post by /////// on 2008-10-20
Dude why do you want to check the permissions of sources.list? Just open up a root text editor then you will be able to edit it without changing its permission. To do this open terminal and type gksu gedit /etc/apt/sources.list
If however you insist on changing its permissions I think you should try chmod 777 instead of chmod ug+rw

---

### Post by Hangwire on 2008-10-20
Hm. Dolphin is a KDE File Manager right?
I get the feeling you are using Kubuntu then. 
Try

```
kdesudo dolphin
```

Although im not familiar with KDE.

Run Dolphin as root:

```
sudo dolphin
```

---

### Post by drew boardman on 2008-10-20
Thanks for that, it now works.  I did not have gksu installed.

---

### Post by geirha on 2008-10-20
> **/////// said:**
> If however you insist on changing its permissions I think you should try chmod 777 instead of chmod ug+rw

No, chmod 777 is always bad advice. Giving everyone write access to sources.list opens the possibility for low privileged users of adding their own repository with malicious packages to the sources.list.

---

### Post by /////// on 2008-10-20
He said he was the 'sole' user so unless he like hosts a web server I don't see how it could be dangerous

---

### Post by ajgreeny on 2008-10-20
The simplest way is to open your text editor as root with ```
kdesu kate /etc/apt/sources.list
```or ```
gksudo gedit /etc/apt/sources.list
```and save your changes that way.  I agree with ///////, you have absolutely no need to change permissions on the file.

---

### Post by geirha on 2008-10-20
> **/////// said:**
> He said he was the 'sole' user so unless he like hosts a web server I don't see how it could be dangerous

What if he decides to install a web server sometime in the future? Would you have remembered that that particular file is writeable to all? Better safe than sorry.

---

