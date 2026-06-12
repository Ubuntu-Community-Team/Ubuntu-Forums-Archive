---
title: "Install local deb packages"
date: 2008-10-16
forum: General Help
---

### Post by liangzan on 2008-10-16
Hi,

I tried installing a local deb package on Ubuntu Hardy. There's a archived forum thread on this problem

[http://ubuntuforums.org/showthread.php?t=297910](http://ubuntuforums.org/showthread.php?t=297910)

But I tried another way. I put the deb package in /var/cache/apt/archives/

Then I called aptitude install <some_package>. And it works. Aptitude is able to find it and install it. 

The question is: am I doing this the right way? Are all my dependency issues taken care of?

---

### Post by pedro_orange on 2008-10-16
Why not just download the dependencies using apt, and then install the deb?

When you run the .deb it should tell you what you're missing. You can either apt-cache for them, or search through [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for the files you need.

If you need further help, please tell me what application you're trying to install and the dependencies missing and I can advise further.

---

### Post by kpkeerthi on 2008-10-16
> **liangzan said:**
> Hi,

I tried installing a local deb package on Ubuntu Hardy. There's a archived forum thread on this problem

[http://ubuntuforums.org/showthread.php?t=297910](http://ubuntuforums.org/showthread.php?t=297910)

But I tried another way. I put the deb package in /var/cache/apt/archives/

Then I called aptitude install <some_package>. And it works. Aptitude is able to find it and install it. 

The question is: am I doing this the right way? Are all my dependency issues taken care of?

You don't have to do it that way. Download the deb file to a folder of your choice and double-click on it. Installation should begin (gdebi installer). If there are dependencies you will be notified and the installation stops. You then have to manually track the required dependent debs and download them all to the same folder as before and run:
```
sudo dpkg -i *.deb
```
in the folder where the debs have been copied and you are done.

In your case, if aptitude finished the installation, it already took care of the dependencies or they were no dependencies at all.

---

