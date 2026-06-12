---
title: "Crash during Inkscape install: now every update gives ubprocess post-installation scr"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by bopomofo on 2009-06-30
Jaunty recently crashed while installing Inkscape. While trying to reinstall the packages I kept getting an error:

subprocess post-installation script returned error exit status 2
 
I finally overcame this with a 

sudo apt-get install inkscape

However, now when I'm running the Update Manager, I get a similar error no matter what is being installed. For example:

E: python-lxml: subprocess post-installation script returned error exit status 2
E: python-numpy: subprocess post-installation script returned error exit status 2
E: python-uniconvertor: subprocess post-installation script returned error exit status 2

However, it "seems" as though the packages are being installed. (They don't show up again in Update Manager).

What gives?

---

### Post by bopomofo on 2009-07-07
After a few more upgrades I've realized that it is **always** the same three packages that are causing a problem:

python-lxml python-numpy python-uniconvertor

As per this thread: [http://ubuntuforums.org/showthread.php?t=863056](http://ubuntuforums.org/showthread.php?t=863056)

Running

```
sudo dpkg -P python-lxml
```

outputs

```
(Reading database ... 204924 files and directories currently installed.)
Removing python-lxml ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing python-lxml (--purge):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python-lxml

```

That same thread suggests running

```
dpkg-divert --list
```

But the packages that are causing problems **do not** show up in the output of that command.

The same thread suggests editing the file /var/lib/dpkg/info/python-lxml.postrm but that file **does not exist**. There is only:

```
python-lxml.list     python-lxml.postinst  python-lxml.prerm
python-lxml.md5sums  python-lxml.preinst

```

All of these except python-lxml.list are **empty**.

Any ideas are much appreciated.

---

### Post by bopomofo on 2009-07-15
Since none of the linked-to solution were working for me, I just decided to remove the offending entries manually:

```
cd /var/lib/dpkg/info/
sudo rm python-lxml.*
sudo rm python-numpy.*
sudo rm python-uniconvertor.*

```

Then from Synaptic Package Manager I was able to remove/reinstall these three packages. Inkscape is still able to launch. Software Update no longer complains about these three packages.

Advice: Don't let your computer crash during a software install from Add/Remove... :mad:

---

