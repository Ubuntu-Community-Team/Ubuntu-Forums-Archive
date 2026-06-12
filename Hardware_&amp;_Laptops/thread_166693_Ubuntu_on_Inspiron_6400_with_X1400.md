---
title: "Ubuntu on Inspiron 6400 with X1400"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by Xanth on 2006-04-26
Hello everyone,

Please note that I have no previous Linux experience and I'm a complete noob.  I looked through your forums for a solution and the ones that I found were for the GMA915 video cards.  Anyway, I tried installing Ubuntu 5.10 on a Inspiron 6400 (The one with Mobility Radeon X1400) and it gave me this error:


Windows System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 9, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
  Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
  to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
Markers: (--) probed, (**) from config file, (==) default setting,
   (++) from command line, (!!) notice, (II) informational,
   (WW) warning, (EE) error, (NI) not implemented, (??) unkown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 26 19:37:21 2006
(==) Using config file: "/etc/X11/xorg.conf"
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No symbols found
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No symbols found
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No symbols found
(EE) No devices Detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
  at [http://wiki.X.Org](http://wiki.X.Org)
for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by nolongerlivecd on 2006-04-27
I think you should try the ATi drivers instead. Much better, and I think they support Mobility 1400 now

---

### Post by Xanth on 2006-04-27
Thanks for the reply.

How exactly do I install the Mobility Radeon 1400 drivers?  When I try to log onto the graphical interface (it loads up Ubuntu, all the normal stuff "Ok's"..etc. and when it tries to get to the user log-in) it gives me the error.

Thanks in advance.
-Sohail

---

### Post by anandakatze on 2006-04-29
To get X working initially, edit /etc/X11/xorg.conf and under section "Device" change "ati" to "vesa" to use the standard VESA driver.
I did get 2D acceleration working with the ATI drivers later (see my experience at [http://individual.utoronto.ca/jaelle_kitty/inspiron6400/](http://individual.utoronto.ca/jaelle_kitty/inspiron6400/)) but haven't had any success with 3D acceleration yet.

---

### Post by nolongerlivecd on 2006-04-29
I downloaded it from the net, at the ATi website

---

### Post by emkay84 on 2006-04-30
[QUOTE=nolongerlivecd]I downloaded it from the net, at the ATi website[/QUOTE]

is this the software
> ati-driver-installer-8.24.8-x86_64.run

how to install it in command

---

### Post by emkay84 on 2006-04-30
[QUOTE=anandakatze]To get X working initially, edit /etc/X11/xorg.conf and under section "Device" change "ati" to "vesa" to use the standard VESA driver.
I did get 2D acceleration working with the ATI drivers later (see my experience at [http://individual.utoronto.ca/jaelle_kitty/inspiron6400/](http://individual.utoronto.ca/jaelle_kitty/inspiron6400/)) but haven't had any success with 3D acceleration yet.[/QUOTE]

when i type the /etc/X11/xorg.conf  it show that the permissoin is denied
so i cant change the ati to vesa.

can someone help me solve this problem

---

### Post by Xanth on 2006-04-30
Hello,

I tried editing it, mind you I am a complete noob.

# edit /etc/x11/xorg.conf
Warning: Unkown Mime-type for "/etc/x11/xorg.conf" -- using "application/*"
Error: no write permission for file "/etc/x11/xorg.conf"

# edit /etc/X11/xorg.conf
Warning: unkown mime-type for "etc/X11/xorg.conf" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

# /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf : Permission denied


Any help appreciated.

Thanks in advance.
-Sohail

---

### Post by anandakatze on 2006-05-01
Try (without quotes) "sudo nano /etc/X11/xorg.conf"

---

### Post by Xanth on 2006-05-02
Alright, thank you very very much for your help so far.

But yet again I'm stuck.

I'm in this
GNU nano 1.3.8         File: etc/X11/xorg.conf          Modified

*Blank Black Screen*

^G Get Help  ^O WriteOut ..etc.
^X Exit         ^J Justify    ..etc.

Of course I don't know how to do that ^G thing, and in the blank black screen I can type stuff.

Help please!

Thanks in Advance. (I apologize for my noob factor.)

---

### Post by RoninGurl on 2006-05-02
I'm having a very similar problem with the Dell Inspiron E1505, with ATI X1300.

---

### Post by anandakatze on 2006-05-02
^G Get Help  ^O WriteOut ..etc.
^X Exit         ^J Justify    ..etc.

To save a file, ^O stands for Control-O, and to exit the nano text editor, ^X stands for Control-X.

Also, make sure you have that initial forward slash / when you specify /etc/X11/xorg.conf . The forward slash / stands for the root of the Linux filesystem.

As for problems with the X1300, the X1400 is based on the X1300 (I think), so anything that's been suggested in this thread that works for the X1300 should also work for the X1400.

---

### Post by Xanth on 2006-05-02
anandakatze thank you so very very much.

It works!!

Thanks a lot mate.

-Sohail

---

### Post by Xanth on 2006-05-02
Sorry, but another question.

I couldn't find "linux-source-2.6.16.tar.bz2" from kernel.org.  The file I did manage to get was "linux-2.6.16.tar.bz2" and "patch-2.6.17-rc3.bz2"

I tried to do the:

"sudo mv linux-2.6.16.tar.bz2 /usr/src"

But it says: "mv: cannot stat 'linux-2.6.16.tar.bz2': No such file or directory"

Thanks in advance.
-Sohail

---

### Post by anandakatze on 2006-05-03
[QUOTE=Xanth]Sorry, but another question.

I couldn't find "linux-source-2.6.16.tar.bz2" from kernel.org.  The file I did manage to get was "linux-2.6.16.tar.bz2" and "patch-2.6.17-rc3.bz2"

I tried to do the:

"sudo mv linux-2.6.16.tar.bz2 /usr/src"

But it says: "mv: cannot stat 'linux-2.6.16.tar.bz2': No such file or directory"

Thanks in advance.
-Sohail[/QUOTE]

Firstly, you are right: the file is linux-2.6.16.tar.bz2
Secondly, you need to be in the same directory as the location you downloaded the file to.
i.e. if the file is located at /home/ananda/downloads/linux-2.6.16.tar.bz2
then I can change directory to /home/ananda/downloads:

cd /home/ananda/downloads

and then move the file:

sudo mv linux-2.6.16.tar.bz2 /usr/src

---

### Post by Xanth on 2006-05-04
Hello,

Here's what I get:

sohail@sohailubuntulaptop:~$ sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package libncurses5-dev


Any help appreciated.
-Sohail

---

### Post by anandakatze on 2006-05-04
First, try "sudo apt-get update" (without quotes).

Second, if you still can't install the package, try enabling the universe and multiverse ubuntu repositories.

---

### Post by Xanth on 2006-05-04
I'm just watching it update here, I remember trying to do this but with just apt-get udpate.  What does sudo mean?  It seems to be used for everything!

---

### Post by Xanth on 2006-05-04
"sudo: make: command not found"

This is right after I installed the Libncruses5.

I tried: "sudo make menuconfig"

Thanks a lot for all your help so far.

---

### Post by anandakatze on 2006-05-05
sudo allows you to run with the permissions of another user (in this case root, which is equivalent to the Windows Administrator account), for one specific command. In general, one tries to do as much as possible with one's own account, since a mistype using root privileges can be problematic. :-)

Any time you get "command not found", you can search through the list of applications that you can install (either graphically through synaptic, or from the command line, e.g. "apt-cache search make", where "make" is the package you want to install).

---

### Post by Xanth on 2006-05-05
Well thank you a lot for all your help.

What I'm going to do is learn Shell, I've got a book now and there's a lot of internet stuff for it.

You've been insanely helpful and I really appreciate it.  But I don't want to continue bothering you.

Regards
-Sohail

---

