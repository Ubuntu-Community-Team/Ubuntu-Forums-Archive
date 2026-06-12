---
title: "missing apache .list files = failed installation"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by bobmagoo on 2009-01-26
Hello,
I was trying to switch from a manual install of apache to an apt-get version tonight and I deleted all of the manually installed  directories. When I tried to do the standard apt-get install, I got this error saying: 
```
(Reading database ... 
dpkg: serious warning: files list file for package `apache2-mpm-prefork' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libapache2-mod-perl2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `apache2-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `apache2.2-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libapache2-mod-php5' missing, assuming package has no files currently installed.
36787 files and directories currently installed.)
Preparing to replace apache2 2.2.3-4+etch6 (using .../apache2_2.2.3-4+etch6_all.deb) ...
Unpacking replacement apache2 ...
Setting up apache2 (2.2.3-4+etch6) ...

```

After it finishes, I look around for any kind of process like apache2 or http, there's none in /etc/init.d/ nor in /usr/local/apache2/bin/

I've tried everything to get this error to go away or to somehow force the system to regenerate the files including: 
-apt-get clean
-apt-get update
-move /var/lib/dpkg/info to info.bak then run the reinstall and copy newly made files to info.bak, then restore info.bak to info
-create above missing files as blank .info files(makes installer just flat out quit)


Any help or advice would be greatly appreciated, worst case, can someone send me their .list files for the above missing ones so I can see if apt will see no files exist where they should be and download the files again.

Thanks in advance.

---

### Post by bobmagoo on 2009-01-26
Hey,
never mind, I just found a forum this morning that included a fix. For those interested, the solution was that I had to issue 2 commands for ever file that I had missing up there: ```
#: aptitude download <package>
#: dpkg -i <package>
```
I had to tweak the order of packages that i used those commands on because of dependencies, but that's the gist. The original post with this solution is: [HTML]http://ubuntuforums.org/showthread.php?t=47888[/HTML]

Hopes this helps my fellow trigger happy "rm -rf" users :p

---

