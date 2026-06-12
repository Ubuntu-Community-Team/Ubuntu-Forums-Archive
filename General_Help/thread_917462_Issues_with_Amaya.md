---
title: "Issues with Amaya"
date: 2008-09-11
forum: General Help
---

### Post by GrafxStar on 2008-09-11
Hi Guys,
I am running Hardy Heron and have installed Amaya 9.53 and open the program one time and it froze up so I had to do a force quit. Now it will not open at all even after I have completely removed it through Synaptic and reinstalled twice. What do I need to do to fix this issue?:confused:

Thanks,
GrafxStar

---

### Post by Pro-reason on 2008-09-11
There is probably some part of the program still running.

Does the problem persist if you log out / reboot?

---

### Post by GrafxStar on 2008-09-11
Yes is does!

---

### Post by Pro-reason on 2008-09-11
> **GrafxStar said:**
> Yes is does!

OK, run Amaya from the terminal in order to see what error messages it spits out. 

(Copy and paste those errors here so that I can read them.)

Do this:

```

sudo apt-get purge   amaya amaya-data amaya-doc
sudo apt-get install amaya amaya-data amaya-doc
**amaya**

```

---

### Post by GrafxStar on 2008-09-11
No help! It uninstalled and reinstalled but still will not run. Do I need to log off and try to re-install?

---

### Post by GrafxStar on 2008-09-11
I just logged off and it still will not load.

---

### Post by Pro-reason on 2008-09-11
> **GrafxStar said:**
> No help! It uninstalled and reinstalled but still will not run. Do I need to log off and try to re-install?

You missed the entire point of what I asked you to do.

---

### Post by GrafxStar on 2008-09-12
Sorry! I should have paid more attention:

grafxstar@jCrew:~$ sudo apt-get purge   amaya amaya-data amaya-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  amaya* amaya-data* amaya-doc*
0 upgraded, 0 newly installed, 3 to remove and 2 not upgraded.
After this operation, 47.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 226340 files and directories currently installed.)
Removing amaya ...
Purging configuration files for amaya ...
Removing amaya-data ...
Removing amaya-doc ...
grafxstar@jCrew:~$ sudo apt-get install amaya amaya-data amaya-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  amaya amaya-data amaya-doc
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/15.2MB of archives.
After this operation, 47.5MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  amaya
Install these packages without verification [y/N]? y
Selecting previously deselected package amaya.
(Reading database ... 223760 files and directories currently installed.)
Unpacking amaya (from .../amaya_wx-9.53-1_i386.deb) ...
Selecting previously deselected package amaya-data.
Unpacking amaya-data (from .../amaya-data_9.55~dfsg.0-1_all.deb) ...
Selecting previously deselected package amaya-doc.
Unpacking amaya-doc (from .../amaya-doc_9.55~dfsg.0-1_all.deb) ...
Setting up amaya (wx-9.53-1) ...

Setting up amaya-data (9.55~dfsg.0-1) ...
Setting up amaya-doc (9.55~dfsg.0-1) ...
grafxstar@jCrew:~$ amaya
The program 'amaya' is currently not installed.  You can install it by typing:
sudo apt-get install amaya
bash: amaya: command not found

---

### Post by Pro-reason on 2008-09-12
That's very interesting.  It seems to install amaya correctly, but then complains that amaya is not in fact installed.

Do the following command:

```

dpkg -L amaya | grep /bin/

```

That will give you a list of commands provided by the amaya package.  When I do it, I get the following output:

```

/usr/lib/Amaya/wx/bin/amaya
/usr/lib/Amaya/wx/bin/amaya_bin
/usr/lib/Amaya/wx/bin/print
/usr/bin/amaya

```

---

### Post by GrafxStar on 2008-09-12
Here is what I get:

grafxstar@jCrew:~$ dpkg -L amaya | grep /bin/
/usr/lib/Amaya-9.53/wx/bin/amaya
/usr/lib/Amaya-9.53/wx/bin/print
/usr/bin/amaya-wx

---

### Post by Pro-reason on 2008-09-12
I see that your version of Amaya is *wx-9.53-1*, whereas mine is *9.55~dfsg.0-1*.  We are both on Hardy, so it ought to be the same.  My version works, but yours is broken.

Have you enabled any extra repositories?

Perhaps you could tell me the output of &#8220;*uname -a && cat /etc/lsb-release*&#8221;.

---

### Post by GrafxStar on 2008-09-12
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

---

### Post by Pro-reason on 2008-09-12
> **GrafxStar said:**
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

OK, that's the output of “cat /etc/lsb-release”, but what about “uname -a”?  And what about my other questions?

---

### Post by GrafxStar on 2008-09-12
Package List

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)   free  non-free
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  partner (source code )
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)  free  non-free
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  partner
Banshee
Cairo Dock
Compiz Fusion

---

### Post by GrafxStar on 2008-09-12
uname -a && cat /etc/lsb-release
Linux jCrew 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

---

### Post by Pro-reason on 2008-09-12
> **GrafxStar said:**
> Package List

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)   free  non-free
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  partner (source code )
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)  free  non-free
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  partner
Banshee
Cairo Dock
Compiz Fusion

That's not the full list.

Please post the full output of “cat /etc/apt/sources.list”.

Use the **#** button on the toolbar to put [noparse]```
...
```[/noparse] tags around it for legibility.

---

### Post by GrafxStar on 2008-09-12
```
deb http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse

deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted

deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted

deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock #Cairo Dock
deb http://ppa.launchpad.net/compiz/ubuntu hardy main #Compiz Fusion
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main #Banshee
deb http://packages.medibuntu.org/ hardy free non-free

#ULTAMATIX REPOS START

# deb http://repoubuntusoftware.info harty all

deb-src http://us.archive.ubuntu.com/ubuntu hardy-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu hardy-updates multiverse

deb-src http://us.archive.ubuntu.com/ubuntu hardy multiverse

deb http://us.archive.ubuntu.com/ubuntu hardy multiverse

# deb http://repoubuntusoftware.info harty all

deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb-src http://security.ubuntu.com/ubuntu hardy-security universe

deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted

deb-src http://archive.canonical.com/ubuntu hardy partner
#ULTAMATIX REPOS END
```

---

### Post by Pro-reason on 2008-09-12
OK, you confused me there.

The “deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty” repo is marked as being disabled (with a “#” sign), so I didn't look into it at first.

But then I enabled it for myself, and found that it is indeed the source of the problem.  You must have disabled it between installing amaya and showing me the source.list file.

Keep it disabled, and do this:

```

sudo apt-get purge amaya
sudo apt-get update
sudo apt-get install amaya

```

That should fix it.

That “Ultimate Edition” repo looks rather suspicious to me.  It's all rather amateurishly done.  Stick to real Ubuntu.

---

### Post by GrafxStar on 2008-09-12
> **Pro-reason said:**
> 

That &#8220;Ultimate Edition&#8221; repo looks rather suspicious to me.  It's all rather amateurishly done.  Stick to real Ubuntu.


That is because I am still very new to Ubuntu. I am a converted Windows user of many, many years! 

I really appreciate your help! It finally worked! Thanks for sticking with it and being patient!

Kudo's to you Sir!

---

### Post by Shobuz99 on 2008-09-12
Hi Pro-reason,

I' also having a problem with Amaya 9.55. 
If I start it from the applications>internet list or the
applications>programming list (it is listed in both places),
Amaya opens and displays on screen, my mouse cursor freezes,
and then Amaya disappears from the screen after 5 seconds or so.
It apparently closes, but issues no error or reason.

Here's some output of the commands you suggested for GrafxStar:

rick@rick-desktop:~$
 dpkg -L amaya | grep /bin/
/usr/lib/Amaya/wx/bin/amaya
/usr/lib/Amaya/wx/bin/amaya_bin
/usr/lib/Amaya/wx/bin/print
/usr/bin/amaya

rick@rick-desktop:~$ uname -a && cat /etc/lsb-release
Linux rick-desktop 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

rick@rick-desktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
rick@rick-desktop:~$ 

Any ideas why Amaya 9.55 is behaving this way for me?

Thank you for any help and advice..
Rick (shobuz99)

---

### Post by Pro-reason on 2008-09-12
Rick, can you tell me exactly what package Amaya is installed from (do “*dpkg -p amaya | grep Version*” to find out)?

It should be “*9.55~dfsg.0-1*”.

Instead of using the menus, run Amaya from the command line (just type “amaya”).  That way you'll get error messages that we can learn from.

---

### Post by GrafxStar on 2008-09-12
Okay Here you go!

```
grafxstar@jCrew:~$ dpkg -p amaya | grep Version
Version: 9.55~dfsg.0-1

```


```
 (amaya_bin:7187): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed

```

although this critical error occurs the software does load and function.

GrafxStar

---

### Post by Shobuz99 on 2008-09-12
> **Pro-reason said:**
> Rick, can you tell me exactly what package Amaya is installed from (do “*dpkg -p amaya | grep Version*” to find out)?

It should be “*9.55~dfsg.0-1*”.

Instead of using the menus, run Amaya from the command line (just type “amaya”).  That way you'll get error messages that we can learn from.

Pro-reason,
Here's the version results:

rick@rick-desktop:~$ dpkg -p amaya | grep Version
Version: 9.55~dfsg.0-1

Then the results of running Amaya from command line:

rick@rick-desktop:~$ amaya
04:41:27 PM: Deleted stale lock file '/home/rick/.amaya_bin-rick'.

(amaya_bin:9407): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
0000:   f0000001  00000300  f0000006  00000000
0010:   f000000b  00000000  f000000c  00367d58
0020:   f000000d  00367d58  f000000e  81240124
0030:   f0000002  00000004  f0000003  00000004
0040:   f0000004  01c9023a  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
*** Amaya: Irrecoverable error ***Aborted
rick@rick-desktop:~$ 

uh...:-s :? :-k any ideas?
thanks
Rick (shobuz99)

---

### Post by Pro-reason on 2008-09-12
Thanks, Rick.

Does it still do it if you do the following?
```

rm -fr ~/.amaya*
sudo apt-get install --reinstall amaya amaya-data

```

---

### Post by GrafxStar on 2008-09-13
Yes it does.

```
(amaya_bin:12201): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed

```

---

### Post by Pro-reason on 2008-09-13
> **GrafxStar said:**
> Yes it does.

```
(amaya_bin:12201): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed

```

I wasn't talking to you!  Are you called Rick too?  Haha.

Your minor error message about Gtk doesn't matter.  It's a common occurrence.  As long as it doesn't make Amaya fail to start, don't worry about it.  If you start it from the menus, you won't see all that anyway.

Your problem is solved.

I'm interested in solving Shobuz99/Rick's problem now.

---

### Post by GrafxStar on 2008-09-13
LOL, Yes I am Rick as well and I did not snap until I had posted. 

Thanks Again for your help!

---

### Post by Shobuz99 on 2008-09-13
> **Pro-reason said:**
> I wasn't talking to you!  Are you called Rick too?  Haha.

Your minor error message about Gtk doesn't matter.  It's a common occurrence.  As long as it doesn't make Amaya fail to start, don't worry about it.  If you start it from the menus, you won't see all that anyway.

Your problem is solved.

I'm interested in solving Shobuz99/Rick's problem now.

Pro-reason,
The problem is still there. I followed your instructions and this is the entire response:

rick@rick-desktop:~$ rm -fr ~/.amaya*
rick@rick-desktop:~$ sudo apt-get install --reinstall amaya amaya-data
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/4319kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 141434 files and directories currently installed.)
Preparing to replace amaya 9.55~dfsg.0-1 (using .../amaya_9.55~dfsg.0-1_amd64.deb) ...
Unpacking replacement amaya ...
Preparing to replace amaya-data 9.55~dfsg.0-1 (using .../amaya-data_9.55~dfsg.0-1_all.deb) ...
Unpacking replacement amaya-data ...
Setting up amaya-data (9.55~dfsg.0-1) ...
Setting up amaya (9.55~dfsg.0-1) ...

rick@rick-desktop:~$ amaya

(amaya_bin:6556): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
0000:   f0000001  00000300  f0000006  00000000
0010:   f000000b  00000000  f000000c  00367d58
0020:   f000000d  00367d58  f000000e  81240124
0030:   f0000002  00000004  f0000003  00000004
0040:   f0000004  01c9023a  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
*** Amaya: Irrecoverable error ***Aborted
rick@rick-desktop:~$ 

Should I have done anything different?
Is the "fire_buffer: DRM_VIA_PCICMD returned -22" error referring to the problem?

Thanks again for all your help.

Rick (shobuz99)

---

### Post by Pro-reason on 2008-09-14
Shobuz99, do this:

```

gksu gedit /usr/bin/amaya

```

Where it says &#8220;XLIB_SKIP_ARGB_VISUALS=1&#8221; add &#8220;G_SLICE=always-malloc&#8221;.

It will end up looking like this:

```

#!/bin/sh
#
# Script to launch amaya_bin
# Irène Vatton, 2007
#

AMAYA_INSTALLDIR="Amaya"
PREFIX=/usr/lib
AMAYAGUI="wx"

env XLIB_SKIP_ARGB_VISUALS=1 **G_SLICE=always-malloc** $PREFIX/$AMAYA_INSTALLDIR/$AMAYAGUI/bin/amaya_bin ${1+$@}

```

Save and close.

Try running Amaya again.  Does that help?  (It's a suggestion I got from the Amaya mailing list.)

Of course, it shouldn't be necessary.  You are running the same version as us.

The only difference I can see between your system and ours is that you are running Linux kernel *2.6.24-**18**-generic*, whereas GrafxStar and I are running *2.6.24-**19**-generic* and *2.6.24-**21**-386*.  Yours is older.  There is a small chance that upgrading to a more recent kernel would help.

---

### Post by Pro-reason on 2008-09-14
Another thing to try is to make sure that you have the latest versions of all the Amaya dependencies properly installed.

```

sudo apt-get install --reinstall *libc6 libexpat1 libfreetype6 libgcc1 libjpeg62 libpng12-0 libraptor1 libstdc++6 libwww-ssl0 libwxbase2.6-0 libwxgtk2.6-0 zlib1g libgl1-mesa-glx libglu1-mes*a
```

---

### Post by Shobuz99 on 2008-09-14
> **Pro-reason said:**
> Another thing to try is to make sure that you have the latest versions of all the Amaya dependencies properly installed.

```

sudo apt-get install --reinstall *libc6 libexpat1 libfreetype6 libgcc1 libjpeg62 libpng12-0 libraptor1 libstdc++6 libwww-ssl0 libwxbase2.6-0 libwxgtk2.6-0 zlib1g libgl1-mesa-glx libglu1-mes*a
```

Here is the output from running both suggestions. It still loads and aborts (got an internal error when it tried to configure libgcc1):

rick@rick-desktop:~$ gksu gedit /usr/bin/amaya
rick@rick-desktop:~$ sudo apt-get install --reinstall libc6 libexpat1 libfreetype6 libgcc1 libjpeg62 libpng12-0 libraptor1 libstdc++6 libwww-ssl0 libwxbase2.6-0 libwxgtk2.6-0 zlib1g libgl1-mesa-glx libglu1-mesa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 14 reinstalled, 0 to remove and 0 not upgraded.
Need to get 5956kB/10.5MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libc6 2.7-10ubuntu3 [4754kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libgcc1 1:4.2.3-2ubuntu7 [27.5kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libstdc++6 4.2.3-2ubuntu7 [330kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main zlib1g 1:1.2.3.3.dfsg-7ubuntu1 [76.0kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libexpat1 2.0.1-0ubuntu1 [68.3kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libgl1-mesa-glx 7.0.3~rc2-1ubuntu3 [177kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libjpeg62 6b-14 [90.2kB]         
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libpng12-0 1.2.15~beta5-3 [189kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libglu1-mesa 7.0.3~rc2-1ubuntu3 [243kB]
Fetched 5956kB in 11s (521kB/s)                                                
E: Internal Error, Could not perform immediate configuration (2) on libgcc1
rick@rick-desktop:~$ gksu gedit /usr/bin/amayarick@rick-desktop:~$ amaya
09:16:32 PM: Deleted stale lock file '/home/rick/.amaya_bin-rick'.

(amaya_bin:10182): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
0000:   f0000001  00000300  f0000006  00000000
0010:   f000000b  00000000  f000000c  00367d58
0020:   f000000d  00367d58  f000000e  81240124
0030:   f0000002  00000004  f0000003  00000004
0040:   f0000004  01c9023a  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
*** Amaya: Irrecoverable error ***Aborted
rick@rick-desktop:~$ 

How would I upgrade the Unbuntu Linux kernel 2.6.24-18-generic to 19 or 21?
I'll try anything at this point....:???: :-k :cry:
Thanks

Rick (shobuz99)

---

### Post by Pro-reason on 2008-09-14
Hmm.  I can see that it had to download several files, which indicates to me that you might not have the most recent version of everything.

Run “sudo apt-get update” and then try again.  Make sure that Synaptic, “Add and Remove Applications”, Adept, and any other package-managing programs are not open.

I believe that “sudo apt-get dist-upgrade” will probably upgrade your kernel, along with everything else.  You could also try installing the kernel manually.  N.B. I personally have problems with my NVidia graphics card when I upgrade the kernel: I have to reinstall the NVidia drivers.

---

### Post by Shobuz99 on 2008-09-14
> **Pro-reason said:**
> Hmm.  I can see that it had to download several files, which indicates to me that you might not have the most recent version of everything.

Run “sudo apt-get update” and then try again.  Make sure that Synaptic, “Add and Remove Applications”, Adept, and any other package-managing programs are not open.

I believe that “sudo apt-get dist-upgrade” will probably upgrade your kernel, along with everything else.  You could also try installing the kernel manually.  N.B. I personally have problems with my NVidia graphics card when I upgrade the kernel: I have to reinstall the NVidia drivers.

Ok. I did what you suggested:

rick@rick-desktop:~$ sudo apt-get update
[sudo] password for rick: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
rick@rick-desktop:~$ amaya
10:08:03 PM: Deleted stale lock file '/home/rick/.amaya_bin-rick'.

(amaya_bin:11340): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
0000:   f0000001  00000300  f0000006  00000000
0010:   f000000b  00000000  f000000c  00367d58
0020:   f000000d  00367d58  f000000e  81240124
0030:   f0000002  00000004  f0000003  00000004
0040:   f0000004  01c9023a  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
*** Amaya: Irrecoverable error ***Aborted
rick@rick-desktop:~$ sudo apt-get install --reinstall libc6 libexpat1 libfreetype6 libgcc1 libjpeg62 libpng12-0 libraptor1 libstdc++6 libwww-ssl0 libwxbase2.6-0 libwxgtk2.6-0 zlib1g libgl1-mesa-glx libglu1-mesa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 14 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/10.5MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
**E: Internal Error, Could not perform immediate configuration (2) on libgcc1**
rick@rick-desktop:~$ **sudo apt-get install --reinstall libgcc1**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/27.5kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 141434 files and directories currently installed.)
Preparing to replace libgcc1 1:4.2.3-2ubuntu7 (using .../libgcc1_1%3a4.2.3-2ubuntu7_amd64.deb) ...
Unpacking replacement libgcc1 ...
Setting up libgcc1 (1:4.2.3-2ubuntu7) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
rick@rick-desktop:~$ amaya
10:09:47 PM: Deleted stale lock file '/home/rick/.amaya_bin-rick'.

(amaya_bin:11648): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
0000:   f0000001  00000300  f0000006  00000000
0010:   f000000b  00000000  f000000c  00367d58
0020:   f000000d  00367d58  f000000e  81240124
0030:   f0000002  00000004  f0000003  00000004
0040:   f0000004  01c9023a  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
*** Amaya: Irrecoverable error ***Aborted
rick@rick-desktop:~$ **sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

rick@rick-desktop:~$ amaya
10:13:22 PM: Deleted stale lock file '/home/rick/.amaya_bin-rick'.

(amaya_bin:11813): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
0000:   f0000001  00000300  f0000006  00000000
0010:   f000000b  00000000  f000000c  00367d58
0020:   f000000d  00367d58  f000000e  81240124
0030:   f0000002  00000004  f0000003  00000004
0040:   f0000004  01c9023a  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
*** Amaya: Irrecoverable error ***Aborted
rick@rick-desktop:~$ 

Arrrgguh! This is frustrating...
I do appreciate your patience with me, on this.

ummmm.. I forgot how to check the version from term..??
Will it show the kernel version, or do i have to reboot to see the GRUB menu list?

Rick (shobuz99)

---

### Post by Pro-reason on 2008-09-14
You did the right thing by reinstalling libgcc1.

Perhaps if you do &#8220;*sudo apt-get install --reinstall libc6 libexpat1 libfreetype6 libgcc1 libjpeg62 libpng12-0 libraptor1 libstdc++6 libwww-ssl0 libwxbase2.6-0 libwxgtk2.6-0 zlib1g libgl1-mesa-glx libglu1-mesa*&#8221; again, it will work now.

The &#8220;dist-upgrade&#8221; command found that you have no important Ubuntu upgrades to install.  That's fine.  But it means that nothing has changed.  You still have the same kernel.

To upgrade, the best thing to do is probably to do a name search for &#8220;2.6.24&#8221; in Synaptic.  You will see that you have several packages which have &#8220;2.6.24.18&#8221; in the name.  Install a higher version of each package.

For example, you might want to go to version 20.  So, you might note that you have &#8220;linux-backports-modules-2.6.24-18&#8221;, and therefore you install &#8220;linux-backports-modules-2.6.24-20&#8221;.

It will ask you questions as it installs.  You should then reboot.  Depending on the settings in /boot/grub/menu.lst, you may be able to choose a kernel to use at start-up.  Once Ubuntu has finished booting, the &#8220;uname -a&#8221; command will tell you what kernel you are running.

Upgrading your linux kernel is not guaranteed to fix Amaya.  It's just an idea.

---

### Post by Shobuz99 on 2008-09-15
> **Pro-reason said:**
> You did the right thing by reinstalling libgcc1.

Perhaps if you do “*sudo apt-get install --reinstall libc6 libexpat1 libfreetype6 libgcc1 libjpeg62 libpng12-0 libraptor1 libstdc++6 libwww-ssl0 libwxbase2.6-0 libwxgtk2.6-0 zlib1g libgl1-mesa-glx libglu1-mesa*” again, it will work now.

The “dist-upgrade” command found that you have no important Ubuntu upgrades to install.  That's fine.  But it means that nothing has changed.  You still have the same kernel.

To upgrade, the best thing to do is probably to do a name search for “2.6.24” in Synaptic.  You will see that you have several packages which have “2.6.24.18” in the name.  Install a higher version of each package.

For example, you might want to go to version 20.  So, you might note that you have “linux-backports-modules-2.6.24-18”, and therefore you install “linux-backports-modules-2.6.24-20”.

It will ask you questions as it installs.  You should then reboot.  Depending on the settings in /boot/grub/menu.lst, you may be able to choose a kernel to use at start-up.  Once Ubuntu has finished booting, the “uname -a” command will tell you what kernel you are running.

Upgrading your linux kernel is not guaranteed to fix Amaya.  It's just an idea.

ok. I reinstalled ALL the lib files, one at a time, just in case it would matter. It didn't. Ran amaya and got the same error and the program closed.
I looked through my synaptic package list and found that the version '20' is not listed for all the various installs. '19' is there though, and there are a few of the '19' versions that appear to be **[COLOR="DarkGreen"]already installed[/COLOR]** (green check box):

linux-ubuntu-modules-2.6.24-19-generic 2.6.24-19.28
linux-restricted-modules-common 2.6.24.13-19.45
linux-headers-2.6.24-19
linux-headers-2.6.24-19-generic
linux-image-2.6.24-19-generic
linux-restricted-modules-2.6.24-19-generic
linux-ubuntu-modules-2.6.24-19-generic

These are all that are listed for version '20':
virtualbox-ose module for linux-image-2.6.24-20-generic
virtualbox-ose module for linux-image-2.6.24-20-openvz
virtualbox-ose module for linux-image-2.6.24-20-rt
virtualbox-ose modules for linux-image-2.6.24-20-server

Of course, "2.6.24-18-generic" is what comes up in my Menu.lst file at boot. I dual boot between an XP drive and an Ubuntu drive.

What do you think I should do?

Rick (shobuz99)

---

### Post by Pro-reason on 2008-09-15
If you don't have all the necessary packages available, then you probably haven't enabled the necessary “pockets” in Synaptic.  A “pocket” means a part of a repository, such as “backports”, “proposed”, etc. 

Go into Synaptic and go to the menus: Settings &#8594; Repositories.  Enable some pockets (Synaptic doesn't use that term).  Afterwards, click “Reload”.

Or you can edit /etc/apt/source.list manually.

If your VirtualBox package don't match up with your other kernel-related packages, I imagine that could cause trouble with VirtualBox's advanced features.

---

### Post by Shobuz99 on 2008-09-15
> **Pro-reason said:**
> If you don't have all the necessary packages available, then you probably haven't enabled the necessary “pockets” in Synaptic.  A “pocket” means a part of a repository, such as “backports”, “proposed”, etc. 

Go into Synaptic and go to the menus: Settings &#8594; Repositories.  Enable some pockets (Synaptic doesn't use that term).  Afterwards, click “Reload”.

Or you can edit /etc/apt/source.list manually.

If your VirtualBox package don't match up with your other kernel-related packages, I imagine that could cause trouble with VirtualBox's advanced features.

Wow! No it's not fixed yet, but I did update the synaptic package settings and enabled the "backports" and "proposed" check boxes.
Once I reloaded I got a 67 file update and install...lots of files
including 19 and 21 for the 2.6.24 family.

Once that was completed, It asked me to decide what I wanted to do with the menu.lst...use new version or keep the old. Before I answered that,
I tried to go nt the existing menu.lst and save it as a second backup.
I messed up somewhere along the way, and Ubuntu froze up on me...I had to reset. But i was able to recover and finish the install. 

Anyway, I tried Amaya from term, and here's the error I got:

rick@rick-desktop:~$ amaya
10:36:56 PM: Deleted stale lock file '/home/rick/.amaya_bin-rick'.

(amaya_bin:6232): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya_bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 7979 error_code 8 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
rick@rick-desktop:~$ 

I'm not a programmer, obviously, so I'm not sure if I should bother with these instructions. 
What do you recommend?

Thanks for hanging in there with me..I do appreciate it very much.
It's a lot to go through just to find an alternative to Dreamweaver MX 2004!!!! geesh!

Rick (shobuz99)

---

### Post by Pro-reason on 2008-09-15
So you managed to upgrade all packages related to the kernel?  Check, by doing “uname -a”.

Have you tried the other idea that I posted higher up in the thread (editing /usr/bin/amaya)?

> **Shobuz99 said:**
> 
Thanks for hanging in there with me..I do appreciate it very much.
It's a lot to go through just to find an alternative to Dreamweaver MX 2004!!!! geesh!

Rick (shobuz99)

Oh, I thought you just wanted to try Amaya out of curiosity.  I wouldn't recommend it as a Dreamweaver substitute.  They are _extremely_ different programs.

If you want to create websites, there really is no alternative to simply learning (X)HTML and CSS (and later on, ECMAScript and Flash).  I create all my websites in gedit and nano.

---

### Post by Shobuz99 on 2008-09-16
> **Pro-reason said:**
> So you managed to upgrade all packages related to the kernel?  Check, by doing “uname -a”.

Have you tried the other idea that I posted higher up in the thread (editing /usr/bin/amaya)?

Oh, I thought you just wanted to try Amaya out of curiosity.  I wouldn't recommend it as a Dreamweaver substitute.  They are _extremely_ different programs.

If you want to create websites, there really is no alternative to simply learning (X)HTML and CSS (and later on, ECMAScript and Flash).  I create all my websites in gedit and nano.

Pro-reason,
ok here's the output of all points you suggested:

rick@rick-desktop:~$ rm -fr ~/.amaya*
rick@rick-desktop:~$ sudo apt-get install --reinstall amaya amaya-data
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/4319kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 159145 files and directories currently installed.)
Preparing to replace amaya 9.55~dfsg.0-1 (using .../amaya_9.55~dfsg.0-1_amd64.deb) ...
Unpacking replacement amaya ...
Preparing to replace amaya-data 9.55~dfsg.0-1 (using .../amaya-data_9.55~dfsg.0-1_all.deb) ...
Unpacking replacement amaya-data ...
Setting up amaya-data (9.55~dfsg.0-1) ...
Setting up amaya (9.55~dfsg.0-1) ...

[B]Next, I did the editing of the amaya "G_SLICE=always-malloc"
and added it. 
Then the uname -a to check version:[/B]

rick@rick-desktop:~$ gksu gedit /usr/bin/amaya
rick@rick-desktop:~$ uname -a
Linux rick-desktop **2.6.24-21**-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux

**Then I ran Amaya one more time:**

rick@rick-desktop:~$ amaya

(amaya_bin:7820): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya_bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 7979 error_code 8 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
rick@rick-desktop:~$ 

**Still not working.**

Yes, I realize that Amaya is not a replacement for Dreamweaver MX. 
I did just want to try it, out of curiosity...to see if I could adapt
my web editing habits to Amaya. 
I simply don't like coding with text editors; because I'm not that skilled and I am a **visual learner** more than a 'logic learner'.
That may be excuses and whining, but I guess I'm set in my ways... I have been doing web sites since 1996.
I've been using computers since 1974...before there were PC's and Macs, etc. 
I started using mainframes and working with editors for GML (general markup language), a precursor to HTML. 
I've spent many years of my IBM career editing HTML using Notepad, CS3 editor, Tiny editor, Wordpad. etc etc.... I became sick of them all. 
I was an Optical/Electrical Test Engineering Technician, in a mfg. environment from 1984 to 2002. I never had a desire to program (hardware guy). 
So my attitude is not favorable to coding for coding's sake..
I'm not bitching about it...just admitting my short-comings.
I appreciate what you're saying..really.

I do appreciate all you've done to help me with Amaya. Really!
It's beginning to look like it's a lost cause.. 
Maybe some possibilities are left; but you would be the one that would see them..not me.

Thanks again..and let me know if you have any other ideas or whether I did something dumb along the way.. it's possible.

Rick (shobuz99)

---

### Post by Pro-reason on 2008-09-16
I've just realised that you have 64-bit Ubuntu and/or a 64-bit machine.  That could explain why different bugs arise on your machine and mine.  64-bit support is a bit early still.

I've reported this to the Amaya mailing list.

Another thing you could try is going to [http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html), picking any of the .deb files there, downloading it and installing it.  It will replace the version from Synaptic.  It might work.

P.S. On the Amaya list, they are saying that &#8220;9.5&#8221; (from our repositories) is the stable version for Amaya for 64-bit Ubuntu.

---

### Post by Shobuz99 on 2008-09-17
> **Pro-reason said:**
> I've just realised that you have 64-bit Ubuntu and/or a 64-bit machine.  That could explain why different bugs arise on your machine and mine.  64-bit support is a bit early still.

I've reported this to the Amaya mailing list.

Another thing you could try is going to [http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html), picking any of the .deb files there, downloading it and installing it.  It will replace the version from Synaptic.  It might work.

P.S. On the Amaya list, they are saying that &#8220;9.5&#8221; (from our repositories) is the stable version for Amaya for 64-bit Ubuntu.

Pro-reason,
Again, Thank you for everything you have done.
I guess I didn't realize that I have a 64 bit machine..I mean when I bought it, I knew; 
But I forgot about it because I was using Windows at the time and well, it didn't seem to matter. I'm not defending Windows!
I hate Windows...I just got lulled into that "Windows" false security feeling..
Anyway..
I will take your suggestion and try installing from the link you sent.
In the meantime, would it be possible for you to keep me informed about what response you get from the Amaya mailing list?
Also, Do you know if the Ubuntu Forum has a section on 64 bit machines and software that will run on them?
It occurred to me that maybe my failure to get Wine to install Dreamweaver properly is in some way connected to the 64 bit issue?

I do appreciate all your time to work on this for me. 
Please keep in touch

Rick (shobu99)

[B]UPDATE: I tried downloading either deb version from the web site you suggested, and
got an error message saying "wrong architecture". Both files were listed as i386: "amaya_wx-10.0.1-1_i386.deb" and "amaya_10.0.1-0ubuntu1_i386.deb"
No 9.55 64 bit packages were listed, either.[/B]

---

### Post by Pro-reason on 2008-09-17
[64-bit forum]("http://ubuntuforums.org/forumdisplay.php?f=343").

I'll see what I can do.

---

