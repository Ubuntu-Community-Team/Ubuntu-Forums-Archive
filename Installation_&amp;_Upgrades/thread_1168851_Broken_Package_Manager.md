---
title: "Broken Package Manager"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by Stavro on 2009-05-24
Hi All,

I&#8217;ve just successfully installed 9.04 from an official canonical disc which came through the post. The system seems to be working fine, with wireless internet access. However, the synaptic package manager will not install anything, the auto-updates are likewise broken, and similarly the .deb installer for flash-player from Adobe is failing too. Any idea why I&#8217;m having so many broken installs?

Any help would be most appreciated.

Kind Regards,

Steven

---

### Post by oldos2er on 2009-05-24
What error messages are you getting?

---

### Post by tommcd on 2009-05-24
Go to: System > Administration > Software_Sources. Check the main, resticted, universe and multiverse sources. Then click on the updates tab. Check "important security updates" and "recommended updates". Then close the software sources window. You will be prompted to reload the sources, so do that.
Then open a terminal (applications > accessories > terminal) and run:
```
sudo apt-get update
sudo apt-get upgrade
```
Post any error messages you may get.

---

### Post by Stavro on 2009-05-25
> **tommcd said:**
> Go to: System > Administration > Software_Sources. Check the main, resticted, universe and multiverse sources. Then click on the updates tab. Check "important security updates" and "recommended updates". Then close the software sources window. You will be prompted to reload the sources, so do that.
Then open a terminal (applications > accessories > terminal) and run:
```
sudo apt-get update
sudo apt-get upgrade
```
Post any error messages you may get.

Upon the second instruction: "sudo apt-get upgrade" I receive the following error:

```
dpkg: parse error, in file `/var/lib/dpkg/available' near line 21813 package `libavformat52':
 `Depends' field, reference to `libavutil-unstripped-49': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

If it's any help, when trying to run the flash .deb installer, I receive the following error also:

[IMG]http://www.midclyth.supanet.com/Error.png[/IMG]

---

### Post by tommcd on 2009-05-25
> **Stavro said:**
> Upon the second instruction: "sudo apt-get upgrade" I receive the following error:

```
dpkg: parse error, in file `/var/lib/dpkg/available' near line 21813 package `libavformat52':
 `Depends' field, reference to `libavutil-unstripped-49': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Open a terminal and run:
```

sudo dpkg --clear-avail

```
See this for reference:
[https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)
Then try to go ahead and run:
```

sudo apt-get update
sudo apt-get upgrade

```
And see if you can get the updates. If this works, you should also then be able to install packages with apt-get or synaptic package manager.

---

### Post by Stavro on 2009-05-26
Thank you very much, it worked a treat.

---

