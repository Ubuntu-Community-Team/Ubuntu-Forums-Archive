---
title: "[SOLVED] Getting more recent versions of GIMP and Blender?"
date: 2008-11-11
forum: General Help
---

### Post by ragtag on 2008-11-11
I'm running Ubuntu 8.04 and was wondering how the update policy is for programs.

I would like to get a more recent versions of Blender and the GIMP. Will these eventually show up in the updates (I can wait a while), or do I have to either download them and install from source or upgrade to 8.10?

---

### Post by Irihapeti on 2008-11-11
oops: double post!

---

### Post by Irihapeti on 2008-11-11
I don't know about Blender, but you can get a more recent version of GIMP from GetDeb: [http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

When you've downloaded the packages, the easiest way (in my experience) is to install them using the terminal.

cd to the directory where you've downloaded them, then

```
sudo dpkg -i *.deb
```

You don't need to uninstall the older version first.

By the way, make sure you don't have any other .debs in that directory, or you may end up installing those as well!

---

### Post by Teddix2 on 2008-11-12
> **Irihapeti said:**
> I don't know about Blender, but you can get a more recent version of GIMP from GetDeb: [http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

When you've downloaded the packages, the easiest way (in my experience) is to install them using the terminal.

cd to the directory where you've downloaded them, then

```
sudo dpkg -i *.deb
```

You don't need to uninstall the older version first.

By the way, make sure you don't have any other .debs in that directory, or you may end up installing those as well!


Hi all,

tried just that; downloaded GIMP 2.6.1 package, but when when installing as suggested [CODE]... I get a "conflicting packages" error. So I maybe do have to uninstall the old version (GIMP 2.4.5) first?

thanks and cheers.

---

### Post by jespdj on 2008-11-12
You can just download Blender from the [Blender download page](http://www.blender.org/download/get-blender/). It doesn't come in a .deb package, but as a .tar.gz. You just unpack it like this:
```
tar xfz blender-2.48a-linux-glibc236-py25-i386.tar.bz2
```
and run the program from the directory that it was unpacked in.

---

### Post by Irihapeti on 2008-11-12
> **Teddix2 said:**
> Hi all,

tried just that; downloaded GIMP 2.6.1 package, but when when installing as suggested [CODE]... I get a "conflicting packages" error. So I maybe do have to uninstall the old version (GIMP 2.4.5) first?

thanks and cheers.

You might be right. I have version 2.6.0, and things might be different with 2.6.1. As I see it, it can't do any harm to uninstall 2.4.5 first.

Irihapeti

---

### Post by ragtag on 2008-11-12
Thanks for the advice.

Searching around a bit I found that Ubuntu 8.10, includes GIMP 2.6.1, which is almost the latest version. Blender was still a little further behind. So maybe I'll just upgrade Ubuntu and then install the latest version of Blender from blender.org

I also think I missunderstood LTS a bit. As I understand it now, it means that bug fixes will keep coming for it, but generally not major new versions of software.

---

### Post by nakama85 on 2008-11-19
> **ragtag said:**
> Thanks for the advice.

Searching around a bit I found that Ubuntu 8.10, includes GIMP 2.6.1, which is almost the latest version. Blender was still a little further behind. So maybe I'll just upgrade Ubuntu and then install the latest version of Blender from blender.org

I also think I missunderstood LTS a bit. As I understand it now, it means that bug fixes will keep coming for it, but generally not major new versions of software.

Here is my tutorial on Gimp 2.6.1
[http://ubuntuforums.org/showthread.php?t=986834](http://ubuntuforums.org/showthread.php?t=986834)

it's just another way to get it done.

---

