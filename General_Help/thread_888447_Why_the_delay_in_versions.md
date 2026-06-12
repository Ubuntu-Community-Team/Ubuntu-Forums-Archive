---
title: "Why the delay in versions ?"
date: 2008-08-13
forum: General Help
---

### Post by anjanesh on 2008-08-13
Hi

I did a  **sudo apt-get install php5 php5-cli**
But the PHP version thats installed is ver 5.2.4.

Why the delay in version when 5.2.5 was released long ago & 5.2.6 released recently which fixes a lot of security vulnerabilities ?

Thanks

---

### Post by hyper_ch on 2008-08-13
Packages will not be upgraded to new versions during a release. Only security fixes will be applied and bugs corrected.

---

### Post by kpkeerthi on 2008-08-13
> Ubuntu releases a new version of its OS every 6 months. After a release, the version of all packages stays constant for the entire 6 months. For example, if Ubuntu ships with OpenOffice.org 2.0.x, it will remain at OpenOffice.org 2.0.x for the entire 6-month release cycle, even if a later version gets released during this time. The Ubuntu team may apply important security fixes to 2.0.x, but any new features or non-security bugfixes will not be made available. ...from [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by ibutho on 2008-08-13
Some distro e.g. Ubuntu don't upgrade versions after a release. Some like Fedora do and for openSUSE and Mandriva, you have to the option to keep the official release versions or use the build service in the case of openSUSE or the backports repos in the case of Mandriva to get the latest versions of most packages.

---

### Post by anjanesh on 2008-08-14
I edited */etc/apt/sources.list* & uncommented 
**[COLOR=Green]# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse[/COLOR]**
Then I did a **sudo apt-get upgrade -u -t hardy-backports** and I get this :
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libpurple0 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib pidgin pidgin-data
The following packages will be upgraded:
  filezilla filezilla-common filezilla-locales flashplugin-nonfree gimp gimp-data gimp-gnomevfs gimp-python libgimp2.0 transmission-common transmission-gtk
11 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 18.6MB of archives.
After this operation, 3351kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```
How come it didnt mention the rest like Apache (from 2.2.8 to 2.2.9) , PHP, MySQL etc etc ?

Thanks

---

### Post by ibutho on 2008-08-14
> How come it didnt mention the rest like Apache (from 2.2.8 to 2.2.9) , PHP, MySQL etc etc ?
It could be that nobody has built those packages and backported them to the version of Ubuntu you are using. From what I understand, the Ubuntu backports repo only contains a limited number of packages and not backports of all the packages available in Ubuntu.

---

### Post by kpkeerthi on 2008-08-14
The backports is community maintained. You may get the latest of your favorite package if you are lucky.

---

### Post by anjanesh on 2008-08-14
This is not good news for a linux newcomer.
For example, FileZilla got updated from 3.0.7.1 to 3.0.11. But the latest release is 3.1.1.1.

1. In Windows, if I had 3.0.7.1 and downloaded & installed 3.1.1.1, it would automatically update *C:\Program Files\FileZilla3* folder.
Is this something I can do on my Ubuntu PC - like download **FileZilla_3.1.1.1_x86_64-linux-gnu.tar.bz2** & install it to automatically replace the current FileZilla from repo ?

2. But now I got to keep a separate directory like /software and have ALL my programs there, building everything whenever a new release is out ?

3. > It could be that nobody has built those packages and backported them to the version of Ubuntu you are using. From what I understand, the Ubuntu backports repo only contains a limited number of packages and not backports of all the packages available in Ubuntu.
> The backports is community maintained. You may get the latest of your favorite package if you are lucky.
Is there any good detailed tutorial to make my own backport packages ?

---

### Post by hyper_ch on 2008-08-14
> **anjanesh said:**
> This is not good news for a linux newcomer.
For example, FileZilla got updated from 3.0.7.1 to 3.0.11. But the latest release is 3.1.1.1.
And what features do you absolutely need from 3.1.1.1 that aer not in 3.0.7.1 or 3.0.11.x?

> **anjanesh said:**
> 1. In Windows
Have a read: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

> Is there any good detailed tutorial to make my own backport packages ?
Search the Ubuntu wiki for "MOTU"... somewhere there it is linked :)

---

### Post by scheuri on 2008-08-14
Hi there....

I keep being amazed how important version numbers seems to "new comers to linux".

First rule:
Most of the distributions (ubuntu, debian, red hat, fedora, SLES, SLED, etc.) come in stable releases.
In other words: at some point the makers of these distribution freeze the "code" or the packages put into a certain release and check for bugs only.
After a certain time they decide that the number of bugs is low enough and release that certain distribution.
So you get releases such as Debian Etch, Debian Lenny or Ubuntu 6.06, 6.10, 7.04, 7.10, 8.04 and so on.

These release contain a certain amount of packages with a certain version number. Sometimes these packages get a little tweaked, but in overall the the version number just stays.
If a newer version comes out of a certain software, your package does NOT get upgraded to this version. It will MAYBE get updated if the new version contained security fixes. The package will stay the very same version, however, will be enhanced with the security fixes.

Eg. PHP version 5.2.4 is in Ubuntu 8.04. There where security fixes in 5.2.5 and 5.2.6.
You will NOT get the new versions with all the features and all the new shiny things, but you will get the security fixes. So your version of php will still be 5.2.4, but with new patchlevels (eg. 5.2.4-1, 5.2.4-2, 5.2.4-3 and so on)

Now, why is this done that way?
Because (debian for example) distributions come with thousand those packages. All have been tested and put together, so they work together.
Now if you change/upgrade one piece of software it needs might very well change. It may need newer versions of another piece of software, so you would need to upgrade this one, too.
With trivial software, this might not happen, but a lot is not that trivial and it would be impossible to maintain a "stable" release.

So, if you want (and actually need?) newer versions of a certaint software, you are surely not a newcomer to linux anymore.
You surely have the chances to get new software, if you really need.
Either using backports (people actually making packages of the new version of software for a certain release, to make it easy to install) or you may compile it yourself.
Or you might even change the distribution to one that actually does change version numbers and upgrades packages (like Gentoo as far as I know).

I am afraid, like everywhere in software (also in windows), it is nearly impossible to be stable and cutting edge at the same time.
It is up to you to decide if you really need that new version with its new features or if you can work with an older version until the next release of the distribution comes out and you may upgrade easy.

My 2 rappen.
Scheuri

Edit: loads of typos

---

### Post by kpkeerthi on 2008-08-14
> **anjanesh said:**
> This is not good news for a linux newcomer.
For example, FileZilla got updated from 3.0.7.1 to 3.0.11. But the latest release is 3.1.1.1.

There are some distros that do update their repos as the new versions of software are released. There was a [discussion]("http://ubuntuforums.org/showthread.php?t=876642") on this topic here in this forum.

You may also want to check out [getdeb]("http://www.getdeb.net/") for some latest packages for hardy.

---

### Post by anjanesh on 2008-08-14
Thank you for your detailed explanation.
> I keep being amazed how important version numbers seems to "new comers to linux". If something doesnt work well in, say FileZilla 3.0.11 & I ask why, the next reply would be to update it to 3.1.1.1 & if it still doesnt work. bump thread.

But there some packages which I still prefer to have the newer releases.
For example, PHP 5.3 which would be released in a couple of months which I definitely like to upgrade to. Its not going to break any of my PHP 5.2 code.

Im reading [this thread]("http://ubuntuforums.org/showthread.php?t=51003") & thinking if its worth it.

---

### Post by deep64blue on 2008-08-14
I would echo what others have said - you don't want random upgrades breaking your system, stability is good.

For my Web Development platform I use XAMPP - [http://www.apachefriends.org/en/index.html](http://www.apachefriends.org/en/index.html) rather than relying on the package management system.

---

### Post by ibutho on 2008-08-14
One thing you can do (and it may help you master Linux) is to compile your own packages from source or build Debian packages using something like checkinstall. You can even share the packages with others when you are done.

---

### Post by anjanesh on 2008-08-14
> One thing you can do (and it may help you master Linux) is to compile your own packages from source or build Debian packages using something like checkinstall. You can even share the packages with others when you are done. This is what I would like to know how to do.
Is [this]("https://help.ubuntu.com/ubuntu/packagingguide/C/") the right place to start ?

---

### Post by ibutho on 2008-08-14
For building Debian packages, take a look [here]("http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html") and [here]("http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html").

---

