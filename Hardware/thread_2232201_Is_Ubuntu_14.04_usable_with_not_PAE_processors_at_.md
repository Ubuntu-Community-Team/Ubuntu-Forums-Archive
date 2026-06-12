---
title: "Is Ubuntu 14.04 usable with not PAE processors at all?"
date: 2014-06-30
forum: Hardware
---

### Post by A.N.S-Ch. on 2014-06-30
I have a box with Pentium M (it is not a processor with PAE). With the help of 'forcepae' kernel option while installation I got installed and bootable 14.04 Ubuntu Desktop system at my box.

Now I'm trying to do apt-get upgrade. New kernel can not be installed while upgrade because of non-PAE processor. There are some strings from the logs:

```
$ apt-get -f install
...
The following extra packages will be installed:
  linux-image-3.13.0-30-generic
...
Preparing to unpack .../linux-image-3.13.0-30-generic_3.13.0-30.54_i386.deb ...
This kernel does not support a non-PAE CPU.
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-30-generic_3.13.0-30.54_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1

```

Is there a way to use modern Ubuntu versions with non-PAE processor?
I'm not shure - may be LUbuntu have apropriate modern kernels?

---

### Post by sudodus on 2014-06-30
Welcome to the Ubuntu Forums :-)

If you installed with the boot option forcepae after the delimiter '--' it was carried into the installed system and you should be able to upgrade the kernel. If you did not, you can add it now into the file **/etc/default/grub**

Edit {
```
sudo nano /etc/default/grub
```
}

Change the line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash forcepae"
```

run

```
sudo update-grub
```

and reboot.

---

### Post by slickymaster on 2014-06-30
[Bodhi]("http://sourceforge.net/projects/bodhilinux/files/2.4.0/bodhi-2.4.0-nonpae-32.iso/download") (based on Ubuntu LTS) and Crunchbang ([torrent]("http://crunchbang.org/torrents/crunchbang-11-20130506-i486.iso.torrent")) (Debian based) both offer non-PAE versions for download

---

### Post by sudodus on 2014-06-30
Maybe I should also add that standard Ubuntu will probably be rather slow with a Pentium M CPU. I would recommend a flavour with a lighter desktop environment, Lubuntu or Xubuntu (or some other light distro as suggested by slickymaster).

I have an IBM Thinkpad T42 with Pentium M and 1280 MB RAM, and it works well with the Xubuntu 12.04 LTS as well as with Lubuntu and Xubuntu 14.04 LTS. I have also tested Bodhi and it works well too in that computer.

---

### Post by kurt18947 on 2014-06-30
I'll mention a non-*buntu distro but works very much like it.  SolydXD, which is I think an offshoot of LMDE (LinuxMintDebianEdition) will run on a non-PAE machine.


[http://forums.solydxk.com/viewtopic.php?f=4&t=3979](http://forums.solydxk.com/viewtopic.php?f=4&t=3979)
> Hi rjm65

You can take both SolydX or SolydK in 32bit flavour and they will install with the i386 kernel, i.e. NON PAE.

P.S.: You can install a PAE kernel later if you need.

Regards,
ulusu

I have it running on a PIII 1 Ghz. 512 MB. RAM notebook and it works pretty well.

---

### Post by A.N.S-Ch. on 2014-06-30
> **sudodus said:**
> Maybe I should also add that standard Ubuntu will probably be rather slow with a Pentium M CPU...

Yes, You are right. I'm hunting for stability and long term support.
The system will be hugely retuned after installation, in order to be more lighter. But, if it will not have security updates, without massive upgrades of the whole system and so on, it will have no sence for me. The box some times can be used as a small and tiny network service.

With LTS Ubuntu I can have a set of a software and for years do only "apt-get upgrade" without a worry. May be this is not the best idea. I'm trying to understand: is it too hard now to deal with all that things, or the box still can be used with the system.

---

### Post by A.N.S-Ch. on 2014-06-30
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

If you installed with the boot option forcepae after the delimiter '--' it was carried into the installed system and you should be able to upgrade the kernel. If you did not, you can add it now into the file **/etc/default/grub**
...
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash forcepae"
```

run

```
sudo update-grub
```

and reboot.

Thank you! That did the trick.

---

### Post by sudodus on 2014-06-30
> **A.N.S-Ch. said:**
> Yes, You are right. I'm hunting for stability and long term support.
The system will be hugely retuned after installation, in order to be more lighter. But, if it will not have security updates, without massive upgrades of the whole system and so on, it will have no sence for me. The box some times can be used as a small and tiny network service.

With LTS Ubuntu I can have a set of a software and for years do only "apt-get upgrade" without a worry. May be this is not the best idea. I'm trying to understand: is it too hard now to deal with all that things, or the box still can be used with the system.

I'm glad you can upgrade the kernel now :-)

Standard Ubuntu 14.04 has 5 years LTS until April 2019. Lubuntu and Xubuntu (14.04) have 3 years LTS until April 2017. ***I think it should be enough with 3 years support*** with debugging and security updates/upgrades.

If you 'only' use it as a server, you can run ***Ubuntu Server*** without a graphical desktop environment and it will be more responsive. Ubuntu Server 14.04 LTS has 5 years support until April 2019.

Another alternative is to install your system from the little end from the Ubuntu ***mini.iso***, where you add only the program packages that you want.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

