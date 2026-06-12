---
title: "Make VLC play DVDs"
date: 2022-12-31
forum: Hardware
---

### Post by Donnie Love on 2022-12-31
What does it take to make VLC play a simple DVD?

---

### Post by ajgreeny on 2022-12-31
If this DVD is a commercially produced one that you bought you probably need to make sure you have libdvdcss2 installed.

Search these forums for that and you will find the way to install it which I can not easily find and copy to you as I'm on a small Android screen at the moment.

Once that is installed, if VLC does not play DVDs automatically you will need to use the menu item ***Media - Play disk*** then probably point to ***/dev/sr0*** and hit the Play button.

Here's the site you need with the information. 
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Donnie Love on 2022-12-31
I appreciate your response, but that didn't work.

Is there another player that will work?

---

### Post by ajgreeny on 2022-12-31
To simply tell us "that didn't work." doesn't help us much to figure out your problem.

What actually happens and what do you see when you put a DVD in your DVD drive? Does VLC or some other application open automatically; does the drive start to spin or does nothing happen?
Have you tried using any other applications with which to play your DVD?

---

### Post by Donnie Love on 2022-12-31
Sorry, I'm technically inept and completely lost. VLC opens and I can hear the disc spinning. Then nothing, eventually the disc stops spinning.

Sometimes I get this error:

[COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not read -1/4 blocks at 0x01.[/COLOR]
 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr1".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvdsimple:///dev/sr1'. Check the log for details.[/COLOR]
 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not read -1/4 blocks at 0x01.[/COLOR]
 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not read -1/4 blocks at 0x01.

I want to try different applications, but I don't know of any. Tried to install Mplayer with no luck.

This is what I get when I tried to install "[/COLOR]sudo apt-get install libdvdread4"[COLOR=#000000]

donnie@MG130-G:~$ sudo apt-get install libdvdread4
[sudo] password for donnie: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package libdvdread4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdread4' has no installation candidate

[/COLOR][COLOR=#000000][COLOR=#000000]And then this:

donnie@MG130-G:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
sudo: /usr/share/doc/libdvdread4/install-css.sh: command not found[/COLOR]

[/COLOR]

---

### Post by ajgreeny on 2022-12-31
Have you installed the **libdvd-pkg** as shown in that linked site I gave you?
> Ubuntu 15.10 and newer

From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss.

    Install the libdvd-pkg package (no need to add third party repositories) via Synaptic or command line: 

sudo apt install libdvd-pkg && sudo dpkg-reconfigure libdvd-pkg

    Follow libdvd-pkg's instructions to let it download, compile, and install libdvdcss. 
From you posts #5 and #6 it looks as if you tried to install **libdvdread** which is no longer available or needed, rather than libdvd-pkg.

---

### Post by Donnie Love on 2022-12-31
Yes. This is what happens:

```
donnie@MG130-G:~$ sudo apt install libdvd-pkg && sudo dpkg-reconfigure libdvd-pkg
[sudo] password for donnie: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following package was automatically installed and is no longer required:
  libfwupdplugin1
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  autoconf automake autopoint autotools-dev binutils binutils-common
  binutils-x86-64-linux-gnu build-essential debhelper debugedit
  dh-autoreconf dh-strip-nondeterminism dpkg-dev dwz fakeroot g++ g++-11 gcc
  gcc-11 gettext intltool-debian libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libarchive-cpio-perl
  libarchive-zip-perl libasan6 libatomic1 libbinutils libc-dev-bin
  libc-devtools libc6-dev libcc1-0 libcrypt-dev libctf-nobfd0 libctf0
  libdebhelper-perl libdpkg-perl libfakeroot libfile-fcntllock-perl
  libfile-stripnondeterminism-perl libgcc-11-dev libitm1 liblsan0
  libltdl-dev libmail-sendmail-perl libnsl-dev libsigsegv2 libstdc++-11-dev
  libsub-override-perl libsys-hostname-long-perl libtirpc-dev libtool
  libtsan0 libubsan1 linux-libc-dev lto-disabled-list m4 make manpages-dev
  po-debconf rpcsvc-proto
Suggested packages:
  autoconf-archive gnu-standards autoconf-doc binutils-doc dh-make
  debian-keyring g++-multilib g++-11-multilib gcc-11-doc gcc-multilib flex
  bison gdb gcc-doc gcc-11-multilib gcc-11-locales gettext-doc
  libasprintf-dev libgettextpo-dev glibc-doc bzr libtool-doc
  libstdc++-11-doc gfortran | fortran95-compiler gcj-jdk m4-doc make-doc
  libmail-box-perl
The following NEW packages will be installed:
  autoconf automake autopoint autotools-dev binutils binutils-common
  binutils-x86-64-linux-gnu build-essential debhelper debugedit
  dh-autoreconf dh-strip-nondeterminism dpkg-dev dwz fakeroot g++ g++-11 gcc
  gcc-11 gettext intltool-debian libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libarchive-cpio-perl
  libarchive-zip-perl libasan6 libatomic1 libbinutils libc-dev-bin
  libc-devtools libc6-dev libcc1-0 libcrypt-dev libctf-nobfd0 libctf0
  libdebhelper-perl libdpkg-perl libdvd-pkg libfakeroot
  libfile-fcntllock-perl libfile-stripnondeterminism-perl libgcc-11-dev
  libitm1 liblsan0 libltdl-dev libmail-sendmail-perl libnsl-dev libsigsegv2
  libstdc++-11-dev libsub-override-perl libsys-hostname-long-perl
  libtirpc-dev libtool libtsan0 libubsan1 linux-libc-dev lto-disabled-list
  m4 make manpages-dev po-debconf rpcsvc-proto
0 upgraded, 63 newly installed, 0 to remove and 0 not upgraded.
Need to get 138 MB/141 MB of archives.
After this operation, 439 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libsigsegv2 amd64 2.13-1ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 m4 amd64 1.4.18-5ubuntu1
  404  Not Found [IP: 91.189.91.38 80]
Ign:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 autoconf all 2.69-14
Ign:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 autotools-dev all 20180224.1+nmu1
Ign:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 automake all 1:1.16.4-2
Ign:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 autopoint all 0.21-4ubuntu3
Err:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 binutils-common amd64 2.37-7ubuntu1
  404  Not Found [IP: 91.189.91.38 80]
Err:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libbinutils amd64 2.37-7ubuntu1
  404  Not Found [IP: 91.189.91.38 80]
Err:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libctf-nobfd0 amd64 2.37-7ubuntu1
  404  Not Found [IP: 91.189.91.38 80]
Err:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libctf0 amd64 2.37-7ubuntu1
  404  Not Found [IP: 91.189.91.38 80]
Err:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 binutils-x86-64-linux-gnu amd64 2.37-7ubuntu1
  404  Not Found [IP: 91.189.91.38 80]
Err:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 binutils amd64 2.37-7ubuntu1
  404  Not Found [IP: 91.189.91.38 80]
Ign:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates/main amd64 libc-dev-bin amd64 2.34-0ubuntu3.2
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates/main amd64 linux-libc-dev amd64 5.13.0-52.59
Err:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libcrypt-dev amd64 1:4.4.18-4ubuntu1
  404  Not Found [IP: 91.189.91.38 80]
Err:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 rpcsvc-proto amd64 1.4.2-0ubuntu5
  404  Not Found [IP: 91.189.91.38 80]
Err:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libtirpc-dev amd64 1.3.2-2
  404  Not Found [IP: 91.189.91.38 80]
Err:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libnsl-dev amd64 1.3.0-2build1
  404  Not Found [IP: 91.189.91.38 80]
Ign:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates/main amd64 libc6-dev amd64 2.34-0ubuntu3.2
Err:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libcc1-0 amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libitm1 amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libatomic1 amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libasan6 amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 liblsan0 amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libtsan0 amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libubsan1 amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libgcc-11-dev amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 gcc-11 amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libstdc++-11-dev amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 g++-11 amd64 11.2.0-7ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:31 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 make amd64 4.3-4ubuntu1
  404  Not Found [IP: 91.189.91.38 80]
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates/main amd64 libdpkg-perl all 1.20.9ubuntu2.2
Ign:33 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 lto-disabled-list all 16
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates/main amd64 dpkg-dev all 1.20.9ubuntu2.2
Err:35 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 build-essential amd64 12.9ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Ign:36 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libdebhelper-perl all 13.3.4ubuntu2
Ign:37 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libtool all 2.4.6-15
Ign:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libfile-stripnondeterminism-perl all 1.12.0-1
Ign:39 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 dh-strip-nondeterminism all 1.12.0-1
Err:40 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 debugedit amd64 1:5.0-0ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:41 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 dwz amd64 0.14-1build1
  404  Not Found [IP: 91.189.91.38 80]
Err:42 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 gettext amd64 0.21-4ubuntu3
  404  Not Found [IP: 91.189.91.38 80]
Ign:43 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 debhelper all 13.3.4ubuntu2
Err:44 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libfakeroot amd64 1.25.3-1.1ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:45 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 fakeroot amd64 1.25.3-1.1ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:46 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libalgorithm-diff-xs-perl amd64 0.04-6build1
  404  Not Found [IP: 91.189.91.38 80]
Ign:47 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates/main amd64 libc-devtools amd64 2.34-0ubuntu3.2
Err:48 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libfile-fcntllock-perl amd64 0.22-3build5
  404  Not Found [IP: 91.189.91.38 80]
Err:49 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libltdl-dev amd64 2.4.6-15
  404  Not Found [IP: 91.189.91.38 80]
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 autoconf all 2.69-14
  404  Not Found [IP: 91.189.91.38 80]
Err:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-updates/main amd64 libc-dev-bin amd64 2.34-0ubuntu3.2
  404  Not Found [IP: 91.189.91.38 80]
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 autotools-dev all 20180224.1+nmu1
  404  Not Found [IP: 91.189.91.38 80]
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 automake all 1:1.16.4-2
  404  Not Found [IP: 91.189.91.38 80]
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 autopoint all 0.21-4ubuntu3
  404  Not Found [IP: 91.189.91.38 80]
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates/main amd64 libdpkg-perl all 1.20.9ubuntu2.2
Err:33 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 lto-disabled-list all 16
  404  Not Found [IP: 91.189.91.38 80]
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates/main amd64 dpkg-dev all 1.20.9ubuntu2.2
Err:36 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libdebhelper-perl all 13.3.4ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Err:37 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libtool all 2.4.6-15
  404  Not Found [IP: 91.189.91.38 80]
Err:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 libfile-stripnondeterminism-perl all 1.12.0-1
  404  Not Found [IP: 91.189.91.38 80]
Err:39 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 dh-strip-nondeterminism all 1.12.0-1
  404  Not Found [IP: 91.189.91.38 80]
Err:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-updates/main amd64 linux-libc-dev amd64 5.13.0-52.59
  404  Not Found [IP: 91.189.91.38 80]
Err:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-updates/main amd64 libc6-dev amd64 2.34-0ubuntu3.2
  404  Not Found [IP: 91.189.91.38 80]
Err:47 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-updates/main amd64 libc-devtools amd64 2.34-0ubuntu3.2
  404  Not Found [IP: 91.189.91.38 80]
Err:43 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish/main amd64 debhelper all 13.3.4ubuntu2
  404  Not Found [IP: 91.189.91.38 80]
Ign:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-updates/main amd64 libdpkg-perl all 1.20.9ubuntu2.2
Ign:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-updates/main amd64 dpkg-dev all 1.20.9ubuntu2.2
Err:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-updates/main amd64 libdpkg-perl all 1.20.9ubuntu2.2
  404  Not Found [IP: 91.189.91.38 80]
Err:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-updates/main amd64 dpkg-dev all 1.20.9ubuntu2.2
  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsigsegv/libsigsegv2_2.13-1ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsigsegv/libsigsegv2_2.13-1ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/m4/m4_1.4.18-5ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/m4/m4_1.4.18-5ubuntu1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/autoconf/autoconf_2.69-14_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/autoconf/autoconf_2.69-14_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/autotools-dev/autotools-dev_20180224.1%2bnmu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/autotools-dev/autotools-dev_20180224.1%2bnmu1_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/automake-1.16/automake_1.16.4-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/automake-1.16/automake_1.16.4-2_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/autopoint_0.21-4ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/autopoint_0.21-4ubuntu3_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-common_2.37-7ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-common_2.37-7ubuntu1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/libbinutils_2.37-7ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/libbinutils_2.37-7ubuntu1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/libctf-nobfd0_2.37-7ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/libctf-nobfd0_2.37-7ubuntu1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/libctf0_2.37-7ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/libctf0_2.37-7ubuntu1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-x86-64-linux-gnu_2.37-7ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-x86-64-linux-gnu_2.37-7ubuntu1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.37-7ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.37-7ubuntu1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc-dev-bin_2.34-0ubuntu3.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc-dev-bin_2.34-0ubuntu3.2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_5.13.0-52.59_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_5.13.0-52.59_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcrypt/libcrypt-dev_4.4.18-4ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcrypt/libcrypt-dev_4.4.18-4ubuntu1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/rpcsvc-proto/rpcsvc-proto_1.4.2-0ubuntu5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/rpcsvc-proto/rpcsvc-proto_1.4.2-0ubuntu5_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtirpc/libtirpc-dev_1.3.2-2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtirpc/libtirpc-dev_1.3.2-2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnsl/libnsl-dev_1.3.0-2build1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnsl/libnsl-dev_1.3.0-2build1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.34-0ubuntu3.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.34-0ubuntu3.2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libcc1-0_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libcc1-0_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libitm1_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libitm1_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libatomic1_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libatomic1_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libasan6_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libasan6_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/liblsan0_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/liblsan0_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libtsan0_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libtsan0_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libubsan1_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libubsan1_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libgcc-11-dev_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libgcc-11-dev_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/gcc-11_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/gcc-11_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libstdc%2b%2b-11-dev_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/libstdc%2b%2b-11-dev_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/g%2b%2b-11_11.2.0-7ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-11/g%2b%2b-11_11.2.0-7ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/make-dfsg/make_4.3-4ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/make-dfsg/make_4.3-4ubuntu1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/libdpkg-perl_1.20.9ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/libdpkg-perl_1.20.9ubuntu2.2_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lto-disabled-list/lto-disabled-list_16_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lto-disabled-list/lto-disabled-list_16_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.20.9ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.20.9ubuntu2.2_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_12.9ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_12.9ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/debhelper/libdebhelper-perl_13.3.4ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/debhelper/libdebhelper-perl_13.3.4ubuntu2_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libtool_2.4.6-15_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libtool_2.4.6-15_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/strip-nondeterminism/libfile-stripnondeterminism-perl_1.12.0-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/strip-nondeterminism/libfile-stripnondeterminism-perl_1.12.0-1_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/strip-nondeterminism/dh-strip-nondeterminism_1.12.0-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/strip-nondeterminism/dh-strip-nondeterminism_1.12.0-1_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/debugedit/debugedit_5.0-0ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/debugedit/debugedit_5.0-0ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dwz/dwz_0.14-1build1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dwz/dwz_0.14-1build1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.21-4ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.21-4ubuntu3_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_13.3.4ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_13.3.4ubuntu2_all.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/libfakeroot_1.25.3-1.1ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/libfakeroot_1.25.3-1.1ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.25.3-1.1ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.25.3-1.1ubuntu2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-6build1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-6build1_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc-devtools_2.34-0ubuntu3.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc-devtools_2.34-0ubuntu3.2_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libf/libfile-fcntllock-perl/libfile-fcntllock-perl_0.22-3build5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libf/libfile-fcntllock-perl/libfile-fcntllock-perl_0.22-3build5_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libltdl-dev_2.4.6-15_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libltdl-dev_2.4.6-15_amd64.deb)  404  Not Found [IP: 91.189.91.38 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by Donnie Love on 2022-12-31
"From you posts #5 and #6 it looks as if you tried to install **libdvdread** which is no longer available or needed, rather than libdvd-pkg."

I don't know one from another. I'm just trying to follow directions.

---

### Post by howefield on 2022-12-31
If you are running Ubuntu 21.10 you'd be better off on a supported release, I'd suggest an LTS like 22.04 which will keep going till at least 2027 without going end of life. Might give you fewer issues and suit your ineptness better.

---

### Post by ajgreeny on 2022-12-31
Ah!
You appear to be still using the Ubuntu version **impish**, 21.10, which is no longer supported so you will be unable to update further nor install any more packages using apt or apt-get or synaptic.

You **must** either try to update to 22.04, which may not be simple for you as a new user, or clean install 22.04 after backing up all the personal files and folders in your home.
To continue using 21.10 is a huge security risk not only to you but to all users who connect to the internet

---

### Post by Donnie Love on 2022-12-31
Terrific. No it's not easy for me. It's a freaking nightmare every time.

---

