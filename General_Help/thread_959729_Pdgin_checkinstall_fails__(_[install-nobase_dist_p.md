---
title: "Pdgin checkinstall fails:  (*** [install-nobase_dist_pidginiconsDATA] Error 1)"
date: 2008-10-26
forum: General Help
---

### Post by joe56 on 2008-10-26
Trying to compile Pidgin 2.5.2 on Ubuntu 8.04: 

./configure
make
sudo checkinstall

Can anyone provide some insight? Thanks!

```
test -z "/usr/local/share" || mkdir -p -- "/usr/local/share"
 /home/joe/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/16x16/apps/pidgin.png' '/usr/local/share/icons/hicolor/16x16/apps/pidgin.png'
chmod: changing permissions of `/usr/local/share/icons/hicolor/16x16/apps/_inst.8242_': No such file or directory
 /home/joe/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/22x22/apps/pidgin.png' '/usr/local/share/icons/hicolor/22x22/apps/pidgin.png'
chmod: changing permissions of `/usr/local/share/icons/hicolor/22x22/apps/_inst.8251_': No such file or directory
 /home/joe/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/24x24/apps/pidgin.png' '/usr/local/share/icons/hicolor/24x24/apps/pidgin.png'
chmod: changing permissions of `/usr/local/share/icons/hicolor/24x24/apps/_inst.8260_': No such file or directory
 /home/joe/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/32x32/apps/pidgin.png' '/usr/local/share/icons/hicolor/32x32/apps/pidgin.png'
chmod: changing permissions of `/usr/local/share/icons/hicolor/32x32/apps/_inst.8269_': No such file or directory
 /home/joe/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/48x48/apps/pidgin.png' '/usr/local/share/icons/hicolor/48x48/apps/pidgin.png'
chmod: changing permissions of `/usr/local/share/icons/hicolor/48x48/apps/_inst.8278_': No such file or directory
make[4]: *** [install-nobase_dist_pidginiconsDATA] Error 1
make[4]: Leaving directory `/home/joe/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/joe/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/joe/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/joe/Desktop/pidgin-2.5.2/pidgin'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

---

### Post by theeren on 2008-11-07
I have the same problem on Ubuntu 8.10. Trying to compile pidgin-2.5.2. 

```
sudo checkinstall
```
comes up with

```
Installation failed. Aborting package creation.
```

---

### Post by andrew.46 on 2008-11-21
Hi:

```
sudo checkinstall -D --fstrans=no --install=yes 
```

  Andrew

---

### Post by kostkon on 2008-11-21
Why not activating the Backports repository and getting it from there?

---

### Post by loko on 2008-11-21
@theeren: Yes, compiling pidgin 2.5.2 in ubuntu 8.10 is nonsens. because it is in there already.

@joe56: i suggest ./configure --prefix=/usr - this is a better way and i think it will also solve your install-problem.

---

### Post by hackel on 2009-01-07
I am having this same issue.  Unfortunately it appears to be a bug in how checkinstall interacts with the install-sh script.  I never used to have any problem with checkinstall and pidgin, they must have changed something.  You shouldn't use sudo with checkinstall.  I do not want to start installing programs as root as I might end up with files scattered all over the place that I can't account for, or it might overwrite something important.  So I definitely *want* checkinstall's filesystem translation.   I just need a way to make it work with install-sh.  

Anyone familiar with this?

---

### Post by ben2talk on 2009-03-22
I managed to get through a Pidgin 2.5.5 install following instructions - now I'm trying the 'encryption' package. I got the tar.gz and unzipped, 

then I did ./compile - great, dependencies satisfied looking goood

Then...

Checkinstall -D (whatever, changed options)

ending in tears like this:

```
config_ui.c: In function 'PE_populate_key_list_view':
config_ui.c:420: warning: too few arguments for format
make[1]: *** [config_ui.lo] Error 1
make[1]: Leaving directory `/media/Storext3/LINUX/Source/pidgin-encryption-3.0'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

```

---

