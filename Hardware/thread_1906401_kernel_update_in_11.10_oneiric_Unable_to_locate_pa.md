---
title: "kernel update in 11.10 oneiric: Unable to locate package"
date: 2012-01-09
forum: Hardware
---

### Post by alfonso78 on 2012-01-09
hi guys,

I'd like to update the kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) to get bet support for Sandy Bridge in 11.10 oneiric

I tried this:

```

sudo add-apt-repository ppa:kernel-ppa/ppa

```

output:

```

You are about to add the following PPA to your system:
 PPA for Ubuntu Kernel PPA
 Ubuntu Kernel Team Daily Build PPA - this PPA typically contains experimental packages. The quality of these packages is such that you had better know what you're doing. Don't come crying to the kernel team if it kills all of your kittens.
 More info: https://launchpad.net/~kernel-ppa/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.L0wkg5hIxb --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 800AA67AE64A6D9E1859C561A8267963484B044F
gpg: requesting key 484B044F from hkp server keyserver.ubuntu.com
gpg: key 484B044F: public key "Launchpad PPA for Ubuntu Kernel PPA" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```

then:

```

sudo apt-get update
sudo apt-get install linux-image-3.1.4-030104-generic_3.1.4-030104.201111281851_i386 linux-headers-3.1.4-030104-generic_3.1.4-030104.201111281851_i386 linux-headers-3.1.4-030104_3.1.4-030104.201111281851_all

```

and I got:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-image-3.1.4-030104-generic_3.1.4-030104.201111281851_i386
E: Couldn't find any package by regex 'linux-image-3.1.4-030104-generic_3.1.4-030104.201111281851_i386'
E: Unable to locate package linux-headers-3.1.4-030104-generic_3.1.4-030104.201111281851_i386
E: Couldn't find any package by regex 'linux-headers-3.1.4-030104-generic_3.1.4-030104.201111281851_i386'
E: Unable to locate package linux-headers-3.1.4-030104_3.1.4-030104.201111281851_all
E: Couldn't find any package by regex 'linux-headers-3.1.4-030104_3.1.4-030104.201111281851_all'

```

so I tried:

```

sudo apt-get install linux-headers-3.1.4_all linux-headers-3.1.4 linux-image-3.1.4

```

and I got:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-headers-3.1.4_all
E: Couldn't find any package by regex 'linux-headers-3.1.4_all'
E: Unable to locate package linux-headers-3.1.4
E: Couldn't find any package by regex 'linux-headers-3.1.4'
E: Unable to locate package linux-image-3.1.4
E: Couldn't find any package by regex 'linux-image-3.1.4'

```

finally:

```

apt-cache showpkg linux-headers

```

output:

```

Package: linux-headers
Versions:

Reverse Depends:
  fglrx,linux-headers
  nvidia-current,linux-headers
  fglrx-updates,linux-headers
  fglrx,linux-headers
  sl-modem-source,linux-headers
  xtables-addons-dkms,linux-headers
  west-chamber-dkms,linux-headers
  oss4-dkms,linux-headers
  openswan-modules-source,linux-headers
  blcr-dkms,linux-headers
  alsa-source,linux-headers
  nvidia-current-updates,linux-headers
  nvidia-current,linux-headers
  nvidia-96-updates,linux-headers
  nvidia-96,linux-headers
  nvidia-173-updates,linux-headers
  nvidia-173,linux-headers
  fglrx-updates,linux-headers
  fglrx,linux-headers
  bcmwl-kernel-source,linux-headers
  dkms,linux-headers
Dependencies:
Provides:
Reverse Provides:
linux-headers-3.0.0-14-virtual 3.0.0-14.23
linux-headers-3.0.0-14-generic-pae 3.0.0-14.23
linux-headers-3.0.0-14-generic 3.0.0-14.23
linux-headers-3.0.0-14 3.0.0-14.23
linux-headers-3.0.0-13-virtual 3.0.0-13.22
linux-headers-3.0.0-13-generic-pae 3.0.0-13.22
linux-headers-3.0.0-13-generic 3.0.0-13.22
linux-headers-3.0.0-13 3.0.0-13.22
linux-headers-3.0.0-12-virtual 3.0.0-12.20
linux-headers-3.0.0-12-generic-pae 3.0.0-12.20
linux-headers-3.0.0-12-generic 3.0.0-12.20
linux-headers-3.0.0-12 3.0.0-12.20

```

any idea?

---

### Post by searchfgold6789 on 2012-01-09
You could [try from the .deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1.4-oneiric/linux-headers-3.1.4-030104_3.1.4-030104.201111281851_all.deb").

---

### Post by alfonso78 on 2012-01-09
> **searchfgold6789 said:**
> You could [try from the .deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1.4-oneiric/linux-headers-3.1.4-030104_3.1.4-030104.201111281851_all.deb").

thank you.

Yes, I thought about that option but I'd like to learn the correct procedure to update kernel using the PPA.

anyone knows how?

---

### Post by Double.J on 2012-01-09
> **alfonso78 said:**
> thank you.

Yes, I thought about that option but I'd like to learn the correct procedure to update kernel using the PPA.

anyone knows how?

Hi there alphonso78, I may be missing something, but this doesn't look good for the PPA -[packages removed]("http://www.ubuntuupdates.org/ppa/kernel-ppa?dist=oneiric")

So you can either use a .deb, or have a crack at compiling - have a look [here]("http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/")

---

### Post by elliotn on 2012-01-09
> **gnu/mirow said:**
> Hi there alphonso78, I may be missing something, but this doesn't look good for the PPA -[packages removed]("http://www.ubuntuupdates.org/ppa/kernel-ppa?dist=oneiric")

So you can either use a .deb, or have a crack at compiling - have a look [here]("http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/")

I also would like the kernel to update automatically rather than having to download debs every update

---

### Post by alfonso78 on 2012-01-09
> **gnu/mirow said:**
> Hi there alphonso78, I may be missing something, but this doesn't look good for the PPA -[packages removed]("http://www.ubuntuupdates.org/ppa/kernel-ppa?dist=oneiric")

So you can either use a .deb, or have a crack at compiling - have a look [here]("http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/")

Indeed, you're right. The packages have been removed but if you look [here (link)]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") you can see they compile new kernels almost every day! v2.6.32.53.21-lucid has been compiled today.

So what's the point of compiling the kernels and not giving a simple way to install them?

Is not that I'm scared of running sudo dpkg -i on various .deb files, I just would like to understand why a PPA used to be available and it's not anymore...

Compiling the kernel is something I will keep as the very last resort...

ps. check [this (link)]("http://www.howopensource.com/2011/08/how-to-install-linux-kernel-3-1-rc2-oneiric-in-ubuntu-11-04-10-10-and-10-04/") for (possibly) good tips. I'll check tonight if it works. It actually suggests it's ok to install a "precise" (ubuntu 12.04) kernel on oneiric (ubuntu 11.10).

---

### Post by alfonso78 on 2012-01-09
I rest my case, it's written [here]("https://wiki.ubuntu.com/Kernel/MainlineBuilds"):

> To use the mainline kernel as-is you only need to **download **and install the *image*.deb package that corresponds to your architecture, however if you need to build any external modules you also need the correct *header*.deb and *source*.deb packages.

So I guess download it's the only way. No automatic PPA.

By the way, I guess the following note is quite important, but I'm not sure what effect it will have on my system:

> Do mainline kernel builds include Ubuntu specific drivers?
By definition the mainline kernel builds are made from virgin unaltered mainline kernel sources and therefore do not, and should not, include any Ubuntu patches or drivers. There are also no binary drivers for these kernels

---

### Post by MoreOrLess on 2012-01-09
[https://launchpad.net/~ptn107/+archive/ppa](https://launchpad.net/~ptn107/+archive/ppa)

---

### Post by alfonso78 on 2012-01-09
> **MoreOrLess said:**
> [https://launchpad.net/~ptn107/+archive/ppa](https://launchpad.net/~ptn107/+archive/ppa)

Cool!

thanks!

question: in this PPA there are tons of packages. After I add the PPA should I update and then upgrade? Or should I install manually the three packages for kernel?

```

linux-headers-3.2.0-7_3.2.0-7.13_all.deb
linux-headers-3.2.0-7-generic-pae_3.2.0-7.13_i386.deb
linux-image-3.2.0-7-generic-pae_3.2.0-7.13_i386.deb

```

If I upgrade, will I install just the new kernel or all the packages listed?

---

### Post by MoreOrLess on 2012-01-09
I think you'll need to manually install them (and future versions). The PPA is meant to instal an additional kernel to the stock kernel and not interfere with it. It would be nice if the PPA used meta-packages to make upgrading easy like the regular kernel does, but it doesn't.

---

### Post by alfonso78 on 2012-01-09
> **MoreOrLess said:**
> I think you'll need to manually install them (and future versions). The PPA is meant to instal an additional kernel to the stock kernel and not interfere with it. It would be nice if the PPA used meta-packages to make upgrading easy like the regular kernel does, but it doesn't.

great, thanks, I'll try later.

does it mean I have to manually purge it if/when I'll want to upgrade to a newer release of ubuntu?

---

### Post by MoreOrLess on 2012-01-09
Yes, but other than taking up some disk space, it won't affect your system if you have old kernels installed.

---

### Post by alfonso78 on 2012-01-10
Hi,

so I managed to update the kernel using ppa ptn107:


```
sudo apt-add-repository ppa:ptn107/ppa
sudo apt-get update
apt-cache showpkg linux-headers
sudo apt-get install linux-headers-3.2.0-7 linux-headers-3.2.0-7-generic-pae linux-image-3.2.0-7-generic-pae

```

and it seems to work (I rebooted with the new kernel) but I get the following errors from apt-get:

```
Error! Bad return status for module build on kernel: 3.2.0-7-generic-pae (i686)
Consult /var/lib/dkms/alsa-hda/0.201110180203~oneiric1/build/make.log for more information.
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-1.fw for module r8169
```

```
$ cat /var/lib/dkms/alsa-hda/0.201110180203~oneiric1/build/make.log
DKMS make.log for alsa-hda-0.201110180203~oneiric1 for kernel 3.2.0-7-generic-pae (i686)
Tue Jan 10 09:08:40 CET 2012
make -C /lib/modules/3.2.0-7-generic-pae/build M=/var/lib/dkms/alsa-hda/0.201110180203~oneiric1/build modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-7-generic-pae'
  CC [M]  /var/lib/dkms/alsa-hda/0.201110180203~oneiric1/build/patch_analog.o
/var/lib/dkms/alsa-hda/0.201110180203~oneiric1/build/patch_analog.c:5080:14: error: expected declaration specifiers or â...â before string constant
/var/lib/dkms/alsa-hda/0.201110180203~oneiric1/build/patch_analog.c:5082:16: error: expected declaration specifiers or â...â before string constant
/var/lib/dkms/alsa-hda/0.201110180203~oneiric1/build/patch_analog.c:5083:20: error: expected declaration specifiers or â...â before string constant
/var/lib/dkms/alsa-hda/0.201110180203~oneiric1/build/patch_analog.c:5087:11: error: âTHIS_MODULEâ undeclared here (not in a function)
make[2]: *** [/var/lib/dkms/alsa-hda/0.201110180203~oneiric1/build/patch_analog.o] Error 1
make[1]: *** [_module_/var/lib/dkms/alsa-hda/0.201110180203~oneiric1/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-7-generic-pae'
make: *** [all] Error 2

```

I tested sound and it still works. Did I do something wrong?

---

### Post by MoreOrLess on 2012-01-10
Hmm. I would contact the PPA maintainer about that.

---

