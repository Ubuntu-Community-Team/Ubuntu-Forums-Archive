---
title: "no sound in 9.10 on Alienware M17x"
date: 2009-11-23
forum: Hardware
---

### Post by etherealremnant on 2009-11-23
Hello, I have successfully installed Karmic Koala on my M17x but I get no sound. I've messed with alsamixer and it detects my IDT sound chip but no sound comes out of the speakers on the laptop even though the volume control seems to work.

It worked fine on 9.04 (I was running Linux Mint 7) and now it doesn't work at all on 9.10 (including Ultimate Edition 2.4). Was something changed?

I really want to move all my usage to Ubuntu for anything that I can and keep Windows 7 as a back up for things like when I have to use Office 2007 and such or for heavy gaming but without sound, Ubuntu isn't a lot of use to me.

If anyone has any ideas, I'd greatly appreciate it.

---

### Post by etherealremnant on 2009-11-24
Its obviously something with Ubuntu. Sound works just fine on the new Mepis alpha out of the box... Nobody has any idea what it is? I greatly prefer Ubuntu to Mepis but if Mepis works out of the box, I'm going to have to switch distros...

EDIT: Sabayon 5 doesn't work either. I don't know what the deal is... trying openSUSE now... FC12 is a hot mess on this machine... I'm about to just give up on linux and stick with Windows. 

The thing that is frustrating is they all detect it as "nVidia HDA audio" so all the distros are picking up the chip but only Mepis seems to know how to use it...

---

### Post by etherealremnant on 2009-11-25
Well I've tried everything I can think of... There was a kernel patch for my chip released in an older kernel and its still not working. I guess I'm using openSUSE...

---

### Post by Jedbot5000 on 2009-12-23
[B]Alienware m17x ubuntu karma 9.10 no sound - solved!!!!

Dudes...I almost gave up on this most frustrating problem...FINALLY found the solution.[/B] 			 			 			 		 		  		  		Do This....It works!!

Just Copy & Paste...this guy is a genius!!

[http://monespaceperso.org/blog-en/20...1/#comment-452]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/comment-page-1/#comment-452")

 Upgrade Alsa (1.0.22) on Ubuntu Karmic Koala 9.10
December 17th, 2009 by alpho2k | Print Upgrade Alsa (1.0.22) on Ubuntu Karmic Koala 9.10
alsa Ubuntu Karmic Koala 9.10 is coming by default with the version 1.0.20 of Alsa so I decided to upgrade to the last version wich is 1.0.22.

What is Alsa (Advanced Linux Sound Architecture) ?

According to Wikipedia, Alsa is a Linux kernel component intended to replace the original Open Sound System (OSS) for providing device drivers for sound cards. Some of the goals of the ALSA project at its inception were automatic configuration of sound-card hardware, and graceful handling of multiple sound devices in a system, goals which it has largely met.

Installation :

To do this, we must begin by determining our version of alsa as follows :

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.

To avoid problems during the upgrade of Alsa-utils, we need to stop it with the following command :

sudo /etc/init.d/alsa-utils stop
We must then install the necessary tools to compile along with the kernel headers :

sudo apt-get -y install build-essential ncurses-dev gettext xmlto
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev

Then, we go in our personal folder and download alsa-driver, alsa-lib and alsa-utils :

cd ~
rm -rf ~/alsa* ~/.pulse*
wget [ftp://ftp.alsa-project.org/pub/drive...1.0.22.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.tar.bz2")
wget [ftp://ftp.alsa-project.org/pub/lib/a...1.0.22.tar.bz2]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.22.tar.bz2")
wget [ftp://ftp.alsa-project.org/pub/utils...1.0.22.tar.bz2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.22.tar.bz2")

After that, we create a new folder for the compilation and installation of the 3 files. Then, we move the 3 tar files that we just downloaded in this folder :

sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .

Unpack the 3 tar files :

sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*

We compile and install alsa-driver :

cd alsa-driver*
sudo ./configure
sudo make
sudo make install

We compile and install alsa-lib :

cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

We compile and install alsa-utils :

cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

If like me, you got this error during the last “sudo ./configure” :

checking form.h presence... yes
checking for form.h... yes
checking for new_panel in -lpanelw... no
configure: error: panelw library not found

You will need to add those symbolics links (only if you got the error) and restart the installation from the last “sudo ./configure” :

sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
sudo ln -s libncursesw.so.5 /lib/libncursesw.so

Then, we remove the 3 tar files in our personal folder that are not anymore necessary :

rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*

Then, just restart your computer and your alsa version should be 1.0.22!

You can verify that you have now indeed have this version of alsa :

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.
Compiled on Dec 17 2009 for kernel 2.6.31-16-generic (SMP).

Just to be sure everything is well configured, execute this command :

sudo alsaconf

and reboot again!

---

### Post by MajinKa on 2010-01-04
Yeah! He IS a genius, however, I'm getting stuck! Everything is going good until when I'm about to compile alsa-utils :(
Upon typing sudo ./configure on my terminal I get (at the very end) this error:

"
checking for libasound headers version >= 1.0.16... not present
configure: error: Sufficiently new version of libasound not found. Stop.
"

I'm gonna try and go through it to the end, however I don't have high hopes upon getting that error obviously... :(

Please! Help would be greatly appreciated!!!!!!!

-Kudos

.:MajinKa:.

---

### Post by MajinKa on 2010-01-04
Well, I said i wasn't hopeful... and WAS I WRONG!!! Screamed like a banshe when i Heard the longin sound after ReBoot! See, I'm a CGI designer and Musican, and switched to Ubuntu (I'm proud to say, not for convenience alone but for conviction upon the idea of the OSI) so, you might realize how much I needed this!

The Ubuntu community is indeed OUTSTANDING

-Kudos

.:MajinKa:.

---

### Post by Marrkk on 2010-01-04
wish they'd not release a distro with a broken pulseaudio...












[http://marrcuk.blogspot.com/]("http://marrcuk.blogspot.com/")

---

