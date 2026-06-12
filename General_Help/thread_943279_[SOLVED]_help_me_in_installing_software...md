---
title: "[SOLVED] help me in installing software.."
date: 2008-10-10
forum: General Help
---

### Post by aprashanth on 2008-10-10
Hello all


I am a very new to linux..

when i am trying to install any new softwares i get errors stating the dependency problem..

for example let us consider yahoo messenger i am getting a lot of dependency problem..i installed few again i am getting the same dependency problem..

so is there  any command that allows automatically update the dependent files..

tsrinu@tsrinu-desktop:~$ ls
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos
tsrinu@tsrinu-desktop:~$ cd Desktop
tsrinu@tsrinu-desktop:~/Desktop$ ls
libgdk-pixbuf2-ruby_0.17.0~rc1-6_all.deb  sortedlist .zip
octave-ann-030908                         yahoomessenger_3.0build126432.dmg
ph_rev sorted list                        ymessenger_1.0.4_1_i386.deb
softwares
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb 
(Reading database ... 95879 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i libgdk-pixbuf2-ruby_0.17.0~rc1-6_all.deb 
(Reading database ... 95879 files and directories currently installed.)
Preparing to replace libgdk-pixbuf2-ruby 0.17.0~rc1-6 (using libgdk-pixbuf2-ruby_0.17.0~rc1-6_all.deb) ...
Unpacking replacement libgdk-pixbuf2-ruby ...
dpkg: dependency problems prevent configuration of libgdk-pixbuf2-ruby:
 libgdk-pixbuf2-ruby depends on libgdk-pixbuf2-ruby1.8; however:
  Package libgdk-pixbuf2-ruby1.8 is not installed.
dpkg: error processing libgdk-pixbuf2-ruby (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgdk-pixbuf2-ruby

tsrinu@tsrinu-desktop:~/Desktop$ ls
libgdk-pixbuf2-ruby_0.17.0~rc1-6_all.deb              octave-ann-030908    softwares        yahoomessenger_3.0build126432.dmg
libgdk-pixbuf2-ruby1.8_0.17.0~rc1-6ubuntu1_amd64.deb  ph_rev sorted list   sortedlist .zip  ymessenger_1.0.4_1_i386.deb

tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i libgdk-pixbuf2-ruby1.8_0.16.0-10_i386.deb   
Selecting previously deselected package libgdk-pixbuf2-ruby1.8.
(Reading database ... 95879 files and directories currently installed.)
Unpacking libgdk-pixbuf2-ruby1.8 (from libgdk-pixbuf2-ruby1.8_0.16.0-10_i386.deb) ...
dpkg: dependency problems prevent configuration of libgdk-pixbuf2-ruby1.8:
 libgdk-pixbuf2-ruby1.8 depends on libruby1.8 (>= 1.8.6.111); however:
  Package libruby1.8 is not installed.
 libgdk-pixbuf2-ruby1.8 depends on libglib2-ruby1.8 (= 0.16.0-10); however:
  Package libglib2-ruby1.8 is not installed.
dpkg: error processing libgdk-pixbuf2-ruby1.8 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgdk-pixbuf2-ruby1.8


dpkg-deb: `yahoomessenger_3.0build126432.dmg' is not a debian format archive
dpkg: error processing yahoomessenger_3.0build126432.dmg (--install):
 subprocess dpkg-deb --control returned error exit status 2

Errors were encountered while processing:
 yahoomessenger_3.0build126432.dmg
tsrinu@tsrinu-desktop:~/Desktop$ 
tsrinu@tsrinu-desktop:~/Desktop$ clear


can any one please help me with those commands 



























tsrinu@tsrinu-desktop:~/Desktop$ ls
libgdk-pixbuf2-ruby_0.17.0~rc1-6_all.deb              libruby1.8-dbg_1.8.7.72-1_i386.deb  sortedlist .zip
libgdk-pixbuf2-ruby1.8_0.16.0-10_i386.deb             octave-ann-030908                   yahoomessenger_3.0build126432.dmg
libgdk-pixbuf2-ruby1.8_0.17.0~rc1-6ubuntu1_amd64.deb  ph_rev sorted list                  ymessenger_1.0.4_1_i386.deb
libruby1.8-dbg_1.8.7.72-1_i3862.deb                   softwares
tsrinu@tsrinu-desktop:~/Desktop$   yahoomessenger_3.0build126432.dmg
bash: yahoomessenger_3.0build126432.dmg: command not found
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i  ymessenger_1.0.4_1_i386.deb
(Reading database ... 95939 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i libgdk-pixbuf2-ruby1.8_0.16.0-10_i386.deb  
(Reading database ... 95939 files and directories currently installed.)
Preparing to replace libgdk-pixbuf2-ruby1.8 0.16.0-10 (using libgdk-pixbuf2-ruby1.8_0.16.0-10_i386.deb) ...
Unpacking replacement libgdk-pixbuf2-ruby1.8 ...
dpkg: dependency problems prevent configuration of libgdk-pixbuf2-ruby1.8:
 libgdk-pixbuf2-ruby1.8 depends on libruby1.8 (>= 1.8.6.111); however:
  Package libruby1.8 is not installed.
 libgdk-pixbuf2-ruby1.8 depends on libglib2-ruby1.8 (= 0.16.0-10); however:
  Package libglib2-ruby1.8 is not installed.
dpkg: error processing libgdk-pixbuf2-ruby1.8 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgdk-pixbuf2-ruby1.8
tsrinu@tsrinu-desktop:~/Desktop$ ls
libgdk-pixbuf2-ruby_0.17.0~rc1-6_all.deb              libruby1.8-dbg_1.8.7.72-1_i3862.deb  softwares
libgdk-pixbuf2-ruby1.8_0.16.0-10_i386.deb             libruby1.8-dbg_1.8.7.72-1_i386.deb   sortedlist .zip
libgdk-pixbuf2-ruby1.8_0.17.0~rc1-6ubuntu1_amd64.deb  octave-ann-030908                    yahoomessenger_3.0build126432.dmg
libglib2-ruby1.8_0.17.0~rc1-5_i386.deb                ph_rev sorted list                   ymessenger_1.0.4_1_i386.deb
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i libglib2-ruby1.8_0.17.0~rc1-5_i386.deb 
Selecting previously deselected package libglib2-ruby1.8.
(Reading database ... 95939 files and directories currently installed.)
Unpacking libglib2-ruby1.8 (from libglib2-ruby1.8_0.17.0~rc1-5_i386.deb) ...
dpkg: dependency problems prevent configuration of libglib2-ruby1.8:
 libglib2-ruby1.8 depends on libruby1.8 (>= 1.8.7.22); however:
  Package libruby1.8 is not installed.
dpkg: error processing libglib2-ruby1.8 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libglib2-ruby1.8
tsrinu@tsrinu-desktop:~/Desktop$ ls
libgdk-pixbuf2-ruby_0.17.0~rc1-6_all.deb              libruby1.8-dbg_1.8.7.72-1_i3862.deb  sortedlist .zip
libgdk-pixbuf2-ruby1.8_0.16.0-10_i386.deb             libruby1.8-dbg_1.8.7.72-1_i386.deb   yahoomessenger_3.0build126432.dmg
libgdk-pixbuf2-ruby1.8_0.17.0~rc1-6ubuntu1_amd64.deb  octave-ann-030908                    ymessenger_1.0.4_1_i386.deb
libglib2-ruby1.8_0.17.0~rc1-5_i386.deb                ph_rev sorted list 
libruby1.8_1.8.7.72-1_i386.deb                        softwares
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i libruby1.8-dbg_1.8.7.72-1_i386.deb 
(Reading database ... 95955 files and directories currently installed.)
Preparing to replace libruby1.8-dbg 1.8.7.72-1 (using libruby1.8-dbg_1.8.7.72-1_i386.deb) ...
Unpacking replacement libruby1.8-dbg ...
dpkg: dependency problems prevent configuration of libruby1.8-dbg:
 libruby1.8-dbg depends on libruby1.8 (= 1.8.7.72-1); however:
  Package libruby1.8 is not installed.
dpkg: error processing libruby1.8-dbg (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libruby1.8-dbg
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i libruby1.8_1.8.7.72-1_i386.deb    
Selecting previously deselected package libruby1.8.
(Reading database ... 95955 files and directories currently installed.)
Unpacking libruby1.8 (from libruby1.8_1.8.7.72-1_i386.deb) ...
Setting up libruby1.8 (1.8.7.72-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i libruby1.8_1.8.7.72-1_i386.deb    
(Reading database ... 96516 files and directories currently installed.)
Preparing to replace libruby1.8 1.8.7.72-1 (using libruby1.8_1.8.7.72-1_i386.deb) ...
Unpacking replacement libruby1.8 ...
Setting up libruby1.8 (1.8.7.72-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i yahoomessenger_3.0build126432.dmg
dpkg-deb: `yahoomessenger_3.0build126432.dmg' is not a debian format archive
dpkg: error processing yahoomessenger_3.0build126432.dmg (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 yahoomessenger_3.0build126432.dmg
tsrinu@tsrinu-desktop:~/Desktop$ sudo apt-get install  ymessenger_1.0.4_1_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ymessenger_1.0.4_1_i386.deb
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 96516 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -libgdk-pixbuf2 
dpkg: conflicting actions -i (--install) and -l (--list)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i libgdk-pixbuf2 
dpkg: error processing libgdk-pixbuf2 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libgdk-pixbuf2
tsrinu@tsrinu-desktop:~/Desktop$ ls
libgdk-pixbuf2-ruby_0.17.0~rc1-6_all.deb              libruby1.8-dbg_1.8.7.72-1_i3862.deb  sortedlist .zip
libgdk-pixbuf2-ruby1.8_0.16.0-10_i386.deb             libruby1.8-dbg_1.8.7.72-1_i386.deb   yahoomessenger_3.0build126432.dmg
libgdk-pixbuf2-ruby1.8_0.17.0~rc1-6ubuntu1_amd64.deb  octave-ann-030908                    ymessenger_1.0.4_1_i386.deb
libglib2-ruby1.8_0.17.0~rc1-5_i386.deb                ph_rev sorted list 
libruby1.8_1.8.7.72-1_i386.deb                        softwares
tsrinu@tsrinu-desktop:~/Desktop$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 96516 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
tsrinu@tsrinu-desktop:~/Desktop$

---

### Post by hyper_ch on 2008-10-10
is there a reason why you don't install a IM client from the repositories that supports the yahoo protocol?

Besides, where did you get those files from? .dmg is for Mac OS X if I'm not mistaken... .deb usually is for Debian and derivates (like *buntu)...

---

### Post by WWSmith36 on 2008-10-10
There is really no need to download programs from random websites.  All you software you need can easily be installed from the repositories.

All software can be installed from add/remove or synaptic.  For more choices, you should enable the additional repositories in System-> Administration-> Software Sources. Select main, universe, restricted, and multiverse.

I would also recommend some third party respos like medibuntu.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Hope this helps

---

### Post by WWSmith36 on 2008-10-10
All software in the repos and stable and have been packaged to satisfy all depencies as well.  If you are looking for particular program let us know.

For example Pidgin Internet Messenger in your Applications-> Internet supports yahoo messenger, so there is really no need to install it.

---

### Post by aprashanth on 2008-10-20
> **hyper_ch said:**
> is there a reason why you don't install a IM client from the repositories that supports the yahoo protocol?

Besides, where did you get those files from? .dmg is for Mac OS X if I'm not mistaken... .deb usually is for Debian and derivates (like *buntu)...


aprashnath:
while i was trying to install instant yahoo messenger.. it was showing that these packages are needed..Moreover i am a very new user to ubuntu..

i have got a command get-aptinstall--from my friend
this actually collects the required files from the repository..


now the main problem that i am facing is i am not being able to connect to the repository..

---

### Post by aprashanth on 2008-10-20
> **WWSmith36 said:**
> There is really no need to download programs from random websites.  All you software you need can easily be installed from the repositories.

All software can be installed from add/remove or synaptic.  For more choices, you should enable the additional repositories in System-> Administration-> Software Sources. Select main, universe, restricted, and multiverse.

I would also recommend some third party respos like medibuntu.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Hope this helps

i am not able to connect to the repository..
its giving me an  error stating that the connection failed..

---

