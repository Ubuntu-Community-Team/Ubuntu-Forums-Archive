---
title: "Problem installing GTK2 engine (Aurora 1.4)"
date: 2008-08-21
forum: General Help
---

### Post by sh_son on 2008-08-21
It's been a while since I reinstalled Ubuntu because of complexity in installing various programs and errors I got from the terminal.
Anyway, I am back to Ubuntu - I just like the desktop effects! :)

So, I have a problem installing Aurora v1.4 GTK2 engine.
This is output from the terminal while I followed installation instruction from :: [http://phorolinux.com/how-to-install-aurora-gtk-engine-13-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-aurora-gtk-engine-13-on-ubuntu-710-gutsy-gibbon.html)

My Linux distro is; Linux Ubuntu 8.10 Hardy (i386, x86, Intel.)

===========================================================
root@klarhaus-laptop:~/Desktop/build-essential-11.3ubuntu1# cd
root@klarhaus-laptop:~# cd Desktop/aurora-1.4
root@klarhaus-laptop:~/Desktop/aurora-1.4# ./configure --prefix=/usr --enable-animation
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
root@klarhaus-laptop:~/Desktop/aurora-1.4# 
===========================================================

It seems that 'C Compiler' is not installed, I googled around and tried to install 'build-essential' through the Synaptic manager but did not find it in there.

I have a limited internet connection, I'm a boarder from a school and the school has a proxy server + domain blocking filtering system.

Anyone can get me install the 'build-essential' package? or even manually by obtaining that source package and installing it through the terminal?

Thank you in Advance,
                       - Eric.

---

### Post by rainwalker on 2008-08-22
[http://download.opensuse.org/repositories/home:/discotronic/xUbuntu_7.10/i386/gtk2-engines-aurora_1.4-1nano_i386.deb](http://download.opensuse.org/repositories/home:/discotronic/xUbuntu_7.10/i386/gtk2-engines-aurora_1.4-1nano_i386.deb)

There's a .deb

---

