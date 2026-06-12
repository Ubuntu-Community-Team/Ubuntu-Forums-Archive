---
title: "[SOLVED] How to tell which repository a package comes from?"
date: 2008-09-09
forum: General Help
---

### Post by CaptSaltyJack on 2008-09-09
I got this recently while doing an apt-get upgrade:

```

WARNING: The following packages cannot be authenticated!
  libneon27 libneon27-gnutls
Install these packages without verification [y/N]?

```

How can I tell which entry in my /etc/apt/sources.list this libneon comes from?  Strange that I got this warning.. the only 3rd party sources I use are for Webmin, Wine, and SVN 1.5.

---

### Post by Zorael on 2008-09-09
Terminal:
```
$ apt-cache policy libneon27 libneon27-gnutls
```

---

### Post by unutbu on 2008-09-09
If you type ```

apt-cache policy libneon27
```

You might get something like
```

libneon27:
  Installed: (none)
  Candidate: 0.27.2-1~gutsy1
  Version table:
     0.27.2-1~gutsy1 0
        500 [COLOR="Red"]http://archive.ubuntu.com gutsy-backports/universe[/COLOR] Packages
```

You can sometimes clear away the warning about packages not being authenticated by running
```

sudo apt-get update
```

Among other things, the command should download new versions of (I guess the gpg) keys that are used to authenticate packages.

---

### Post by CaptSaltyJack on 2008-09-09
Awesome, thanks!

Is there any way to limit which packages can be upgraded?  This particular libneon27 is coming from ppa.launchpad.net, but I want to keep ppa.launchpad.net in my sources.list for SVN updates.  But I'm not interested in their other packages.  Any way to set restrictions?

---

### Post by unutbu on 2008-09-09
I think the way to do this is with pin priorities. See  [http://ubuntuforums.org/showpost.php?p=3642685&postcount=5](http://ubuntuforums.org/showpost.php?p=3642685&postcount=5)

The link to documentation that newtonfn references is in Spanish. The English version is here: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

bapoumba also describes how to use pinning here:
[http://bapoumba.wordpress.com/2007/10/27/priorities-for-apt-repositories-debian-based-distributions/](http://bapoumba.wordpress.com/2007/10/27/priorities-for-apt-repositories-debian-based-distributions/)

I've never done this myself (some tinkering may be required!), but I think the way you could do it is to make a file called /etc/apt/preferences and put in it
```

Package: libneon27
Pin: release l=launchpad
Pin-Priority: 990

Package: *  
Pin: release l=launchpad
Pin-Priority: 400
```

---

### Post by CaptSaltyJack on 2008-09-09
Thanks!  I have some reading up to do on pinning.

---

### Post by indecisive on 2008-09-09
You could also just use the S.M.A.R.T. package manager, which will show you what repository a package comes from in its interface.

---

### Post by CaptSaltyJack on 2008-09-18
> **unutbu said:**
> I think the way to do this is with pin priorities. See  [http://ubuntuforums.org/showpost.php?p=3642685&postcount=5](http://ubuntuforums.org/showpost.php?p=3642685&postcount=5)

The link to documentation that newtonfn references is in Spanish. The English version is here: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

bapoumba also describes how to use pinning here:
[http://bapoumba.wordpress.com/2007/10/27/priorities-for-apt-repositories-debian-based-distributions/](http://bapoumba.wordpress.com/2007/10/27/priorities-for-apt-repositories-debian-based-distributions/)

I've never done this myself (some tinkering may be required!), but I think the way you could do it is to make a file called /etc/apt/preferences and put in it
```

Package: libneon27
Pin: release l=launchpad
Pin-Priority: 990

Package: *  
Pin: release l=launchpad
Pin-Priority: 400
```

This worked great, thanks!  Unfortunately, wildcards don't work on the package name (Package: libneon27*), so I have to exclude different libneon related stuff separately.

---

