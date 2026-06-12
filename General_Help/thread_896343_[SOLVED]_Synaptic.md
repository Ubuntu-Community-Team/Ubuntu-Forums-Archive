---
title: "[SOLVED] Synaptic?"
date: 2008-08-21
forum: General Help
---

### Post by Yezinki on 2008-08-21
Hi there,

When I installed packages..........Opened Synaptic>Edit>Mark by Task> downloaded packages.

Where are the packages & Live CDs saved??

Thanks in advance!

---

### Post by iaculallad on 2008-08-21
> **Yezinki said:**
> Hi there,

When I installed packages..........Opened Synaptic>Edit>Mark by Task> downloaded packages.

Where are the packages & Live CDs saved??

Thanks in advance!

Try to browse /var/cache/apt/archives:

```
cd /var/cache/apt/archives
```

---

### Post by Yezinki on 2008-08-21
ubuntu@ubuntu-laptop:~$ cd /var/cache/apt/archives
ubuntu@ubuntu-laptop:/var/cache/apt/archives$

---

### Post by iaculallad on 2008-08-21
> **Yezinki said:**
> ubuntu@ubuntu-laptop:~$ cd /var/cache/apt/archives
ubuntu@ubuntu-laptop:/var/cache/apt/archives$

You could issue the **ls** terminal command to view the contents of that folder:

```
ls
```

---

### Post by ad_267 on 2008-08-21
You can also just use the graphical file browser too.

---

### Post by Yezinki on 2008-08-21
There are no Live Cds??

---

### Post by Yezinki on 2008-08-21
> **ad_267 said:**
> You can also just use the graphical file browser too.

how do you use that??

---

### Post by iaculallad on 2008-08-21
> **Yezinki said:**
> how do you use that??

On your terminal:

```
nautilus
```

Or simply open Places->Computer->Filesystem-> and browse through /var/cache/apt/archives

But if you want a privilege window where you can copy/cut/paste folders and files:

```
gksudo nautilus
```

---

### Post by Yezinki on 2008-08-21
ubuntu@ubuntu-laptop:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:7500): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by Yezinki on 2008-08-21
ubuntu@ubuntu-laptop:~$ nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:7648): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown
ubuntu@ubuntu-laptop:

---

### Post by ad_267 on 2008-08-21
Nautilus is for gnome, you're using kde so the equivalent is dolphin I think. But looks like you found that folder fine anyways.

No there aren't any live CDs, only the packages.

If you want to make a Live CD you have to use remastersys. If you just want to be able to save the packages to a cd try using AptOnCD.

---

### Post by Yezinki on 2008-08-21
Thanks where do I get/download remastersys??

Secondly, if iii want ii would have to individual download Ubuntu, Kubuntu, Mythbuntu & Xbuntu

Regards!

---

### Post by ad_267 on 2008-08-21
It's not in the repositories but you can get it from here:
[http://remastersys.klikit-linux.com/repository/remastersys/](http://remastersys.klikit-linux.com/repository/remastersys/)

You can download Kubuntu, Xubuntu etc here: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by Yezinki on 2008-08-21
Thanks ad_267,

How can I get them through

Index of /repository/remastersys

      Name                    Last modified       Size  Description

[DIR] Parent Directory        05-Mar-2008 11:25      -  
[   ] Packages.gz             25-Apr-2008 21:39     1k  
[TXT] remastersys_2.0-1_al..> 07-Jan-2008 14:57    14k  
[TXT] remastersys_2.0-2_al..> 07-Jan-2008 14:57    14k  
[TXT] remastersys_2.0-3_al..> 13-Mar-2008 11:23   141k  
[TXT] remastersys_2.0-4_al..> 19-Mar-2008 23:13   142k  
[TXT] remastersys_2.0-5_al..> 25-Apr-2008 21:39   141k  

Apache/1.3.41 Server at remastersys.klikit-linux.com Port 80

You mean all 4 variants & than burn them on to an optical media?

Regards!

---

### Post by ad_267 on 2008-08-21
You want this file here: [http://remastersys.klikit-linux.com/repository/remastersys/remastersys_2.0-5_all.deb](http://remastersys.klikit-linux.com/repository/remastersys/remastersys_2.0-5_all.deb)

You can double click on it to install remastersys.

Yes that's what I mean. Is that what you are after?

---

### Post by Yezinki on 2008-08-21
Yes thats I am after.

Thanks!

---

### Post by Yezinki on 2008-08-21
> **ad_267 said:**
> You want this file here: [http://remastersys.klikit-linux.com/repository/remastersys/remastersys_2.0-5_all.deb](http://remastersys.klikit-linux.com/repository/remastersys/remastersys_2.0-5_all.deb)

You can double click on it to install remastersys.

Yes that's what I mean. Is that what you are after?

What do I do after have installed remastersys?

Regards!

---

### Post by ad_267 on 2008-08-21
I haven't used it myself. There's a guide here:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

You won't have to do the first steps to install it.

---

### Post by Yezinki on 2008-08-22
Thanks ad_267 I shall give it a try & let you know.

Regards!

---

