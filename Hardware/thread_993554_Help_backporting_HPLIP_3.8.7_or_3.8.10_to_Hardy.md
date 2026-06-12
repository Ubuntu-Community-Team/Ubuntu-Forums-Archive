---
title: "Help backporting HPLIP 3.8.7 or 3.8.10 to Hardy"
date: 2008-11-25
forum: Hardware
---

### Post by jwishnie on 2008-11-25
I am tied to Hardy ('cause of LTS) but need to use new HP printers that are supported only in HPLIP >=2.8.5 (like the Deskjet D2560)

Typically in this situation I would manually backport packages from a later release (Intrepid or Jaunty) into Hardy by compiling via:

On a hardy system:
apt-get source <pkg>
apt-get build-dep <pkg>
debuild -uc -us

But in this case, with the transition of the naming for CUPS packages from '*cupsys*' to '*cups*', the dependencies are all broken.

I know I can download the tar-ball from HP and manually compile, but I like to stay with DEBs for manageability.

Any ideas on how to address the problem and backport the existing DEBs without having to also pull in all the new CUPS packages??

Is anyone planning on backporting HPLIP officially into hardy-backports?

thanks for any help!

- Jeff

---

### Post by kaibob on 2008-11-25
You can download the software from the following site and then install it with the provided command:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

I haven't tried it with the latest release, but it's always worked fine. It's not a deb, but installation couldn't be easier.

---

