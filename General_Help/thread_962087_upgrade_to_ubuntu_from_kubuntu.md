---
title: "upgrade to ubuntu from kubuntu"
date: 2008-10-28
forum: General Help
---

### Post by johnycage on 2008-10-28
I'm using KDE version of ubuntu ie. kubuntu 8.04
But I'm not impressed much with it. 

I had used GNOME Ubuntu earlier & I liked it. I want to now switched back to normal ubuntu & now that new version is coming preferably the new version. So my question is: [B]
How to upgrade (or is there any way to upgrade) from Kubuntu8.04 to Ubuntu8.10?[/B]

The problem I have is I have modified the system a bit, I have installed some applications like google-earth & dont want to do all that again...

help appreciated.

---

### Post by pytheas22 on 2008-10-28
If you open a terminal and type:
```

sudo apt-get install ubuntu-desktop
```

it will download and install all of normal Ubuntu for you.  At the login screen, you would have the option of logging into Gnome or KDE.  If you wanted, you could get rid of KDE by typing:
```

sudo apt-get remove kubuntu-desktop
```

(This should work, but you should check the list of packages that it's going to uninstall just to make sure it's not going to break your system.)  Once you install Gnome/Ubuntu, you can upgrade to 8.10 and it will upgrade everything along with it (or you could upgrade to 8.10 first, then install ubuntu-desktop, which might actually make more sense because you wouldn't waste bandwidth by downloading ubuntu-desktop 8.04 only to download most of it again in the 8.10 version).

---

### Post by johnycage on 2008-10-28
> **pytheas22 said:**
> If you open a terminal and type:
```

sudo apt-get install ubuntu-desktop
```

it will download and install all of normal Ubuntu for you.  At the login screen, you would have the option of logging into Gnome or KDE.  If you wanted, you could get rid of KDE by typing:
```

sudo apt-get remove kubuntu-desktop
```

(This should work, but you should check the list of packages that it's going to uninstall just to make sure it's not going to break your system.)  Once you install Gnome/Ubuntu, you can upgrade to 8.10 and it will upgrade everything along with it (or you could upgrade to 8.10 first, then install ubuntu-desktop, which might actually make more sense because you wouldn't waste bandwidth by downloading ubuntu-desktop 8.04 only to download most of it again in the 8.10 version).

wow! so it seems simple, right?
So no data will be lost, right?
only desktop environment will changed... OK.
Thanks.

But to make problem complicated, I want to ask: **Can I upgrade **(or downgrade ?? :rolleyes: )** to Ubuntu 8.10 32-bit from kubuntu 8.04 64-bit**

---

### Post by pytheas22 on 2008-10-29
Right, in principle, no data would be lost (but of course you should back up important stuff just in case), as you're really only changing the desktop environment and a few related applications.
> 
Can I upgrade (or downgrade ??  ) to Ubuntu 8.10 32-bit from kubuntu 8.04 64-bit 

That would be much more difficult, because it would require replacing virtually every single package and application on your system.  Is there a reason you want to be on 32-bit?  Maybe there's a better solution than downgrading your entire system.

---

### Post by johnycage on 2008-10-29
32-bit OS because I had to do many tweaks to run some application on 64-bit OS. eg.flash player addon at firefox etc.

Still I couldn't operate Skype as it gives x386 compatiblity error on myu 64-bit kubuntu. (I know there must be some solution but I guess everytime I'll have to use some modifications to run such appl) I know it's not a STRONG reason.

I have 2GB RAM & alloted 1 GB as SWAP memory. I guess I can run 32-bit OS well.
But if it's a complex process I'd stick to 64-bit

---

### Post by pytheas22 on 2008-10-29
Yes, the Adobe flash plugin can be a pain because Adobe refuses to release a 64-bit build.  But in Ubuntu 8.04 it should have worked relatively painlessly, at least under Firefox.  If you had to do a lot of extra hacking to get it working, you should start a thread about that, because it shouldn't have been necessary.

Skype is also obnoxious for the same reason.  But if you follow [these instructions]("http://ubuntuforums.org/showthread.php?t=432295") you should be able to get it running.  They've always worked fine for me.

---

### Post by johnycage on 2008-10-30
I tried that code over the command line: But I got this error, please have a look. :( ```
ppa@ppa-laptop:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: gimp-python but it is not going to be installed
                  Recommends: gimp-gnomevfs but it is not going to be installed
E: Broken packages
ppa@ppa-laptop:~$ 
```

---

### Post by pytheas22 on 2008-10-30
This appears to be a weird problem with the package manager--it's getting hung up on the gimp-python package, which is hardly necessary for anything.  Does it work if you type:
```

sudo apt-get install ubuntu-desktop gimp-python
```

It also might work to download and install the [gimp-python]("http://packages.ubuntu.com/hardy/gimp-python") package first,  then run 'sudo apt-get install ubuntu-desktop'.

---

