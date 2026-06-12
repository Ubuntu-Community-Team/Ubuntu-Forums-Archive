---
title: "Linux &amp; Biometrics"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by quark_77 on 2007-04-04
Hi All,

This is more of a general question than a specific problem. My laptop has a Trusted Platform Module and a Fingerprint Scanner. I'm wondering if there is any support under linux to utilise these devices, particularly the finger print reader? Is there any support for other biometric hardware?

Thanks for any links/ideas.

Quark_77

---

### Post by jjordan on 2007-04-04
What model laptop? Do you know which fingerprint scanner you have?  I have a Fujitsu P1510 but this is pretty low on my priority list.  I have done some web surfing.

This page seems to indicate it is possible but non-trivial.
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader)

Here is another:
[http://tuxmobil.org/laptop_fingerprint_reader_linux.html](http://tuxmobil.org/laptop_fingerprint_reader_linux.html)

-j

---

### Post by IcemanV9 on 2007-04-04
Depends on which kind of fingerprint scanner you have.

In your terminal, type ...
```
lsusb
```

If you have "SGS Thomson Microelectronics Fingerprint Reader" in the list, then there might be a good chance for you. Follow the first link from jjordan's post.

If not, then research some more from Google and the second link from jjordan's post.

---

### Post by quark_77 on 2007-04-04
Hi all,

I have a Lenovo Thinkpad R60, lsusb outputs this: Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader So it looks like I'm in luck - I'll have a look at that link and see how I get on,

Thanks,

Quark_77

---

### Post by quark_77 on 2007-04-05
Hello All,

Have downloaded and successfully compiled bioapi following the instructions here: [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader) into the directory /opt/bioapi as that seemed the best place to keep things tidy. 

Now I'm trying to compile pam-bioapi-0.3.0 in order to use it with gdm and I'm running the following command:
```
./configure --libdir=/lib CFLAGS=-I/opt/bioapi/include/

```
All goes smoothly until the end where I get this:
> checking bioapi.h usability... yes
checking bioapi.h presence... no
configure: WARNING: bioapi.h: accepted by the compiler, rejected by the preprocessor!
configure: WARNING: bioapi.h: proceeding with the compiler's result 
checking for bioapi.h... yes
checking bioapi_util.h usability... no
checking bioapi_util.h presence... no
checking for bioapi_util.h... no
configure: error: cannot find required header: bioapi_util.h

Now, assuming it liked the CFLAGS option, which I'm not so sure about, there isn't a bioapi_util.h file anyway!! The following:
```
quark_77@quarkspc:/opt/bioapi/include$ ls
bioapi_api.h  bioapi_schema.h    bioapi_type.h  biospi_type.h
bioapi_err.h  bioapi_spi.h       bioapi_uuid.h  bsp_schema.h
bioapi.h      bioapi_typecast.h  biospi.h
quark_77@quarkspc:/opt/bioapi/include$ 

```
Shows you it doesn't exist anyway.

So then I modified my command to this:
```
sudo ./configure --libdir=/lib CFLAGS=-I/opt/bioapi/include CXXFLAGS=-I/opt/bioapi/include LDFLAGS=-L/opt/bioapi/lib CPPFLAGS=-I/opt/bioapi/include

```
Which removes the above error about preprocessor rejection. Then I copied bioapi_util.h from my bioapi sources into /opt/bioapi/include figuring this would solve the problem. However, I'm still getting:
```
checking bioapi.h usability... yes
checking bioapi.h presence... yes
checking for bioapi.h... yes
checking bioapi_util.h usability... no
checking bioapi_util.h presence... no
checking for bioapi_util.h... no
configure: error: cannot find required header: bioapi_util.h

```
Which means I fixed the first bit but not the second. Any Ideas?

[COLOR="DarkRed"]**_EDIT_**[/COLOR]: Could this be the result of Qt not compiling successfully? I compiled bioapi with the following:
```
./configure --prefix=/opt/bioapi --with-x --with-Qt-dir=no
```

Thanks for your help!

---

### Post by IcemanV9 on 2007-04-06
I have no idea about pam-bioapp-0.3.0 (I did not compile it on my box). I just compiled thinkfinger-0.2.2. And, it worked just fine.

I know thinkfinger-0.3 is out, but I don't have time to try it yet.

---

### Post by quark_77 on 2007-04-07
Even more fantastic than the first time, thinkfinger-0.3 is out, I've compiled & installed it and can now enroll users easier than on windows... no bioapi / pam_bioapi needed the software comes with all it needs ready, just a short compile!!

Thanks for all your links guys!!

Quark_77

---

### Post by quark_77 on 2007-04-12
Hi IcemanV9,

I'm wondering, now I've got thinkfinger-0.3 working, if the version you have has the same problem with gksu as I have? Any shortcut running gksu kills the pam_thinkfinger module - so for example, if I click synaptic, it doesn't appear first time but shows its loading thing in the taskbar. Second time, gksu shows and now fingerprint authentication with sudo and logging in doesn't work, a reboot cures this problem.

Any ideas? Perhaps integration with gksu will be in a future release, I'll check on the web site...

---

### Post by IcemanV9 on 2007-04-13
I think it is a known bug for a while. I have a same problem with 0.2.2 & gksudo (it worked despite few errors messages).

---

### Post by DagMan on 2007-04-26
if I kill gksu as root then I have my fingerprint reader back straight away.

I've tried replacing gksu with a bash script that does xterm -e "sudo $1" which asks for the prompt in an xterm but for example if I want to leave firestarter in the system tray then I'm stuck with an xterm open as well.  It's a start and surely there's a way to do something like this workably.

---

### Post by DagMan on 2007-04-27
EDIT:  This post had an insecure workaround.

---

### Post by DagMan on 2007-04-28
The above isnt' a good solution, anything with command line options to gksu didn't work and I intended to look into adding handlers for it using the equivalent sudo option but on reboot I was prompted by zenity to add something that didn't have anything in it at all.  It effected the time it took for panels to load and respond too.

It's a start if someone else wants to add some input.  For now I think I'm stuck having to rename the above little gksu script to something else and tell menu items to call the script by it's new name.  Sort of a pain to do the menu editing and I'm sure there's an easy way to do it at the command line but I don't know how.

---

### Post by DagMan on 2007-04-29
This seems to work fine and just needs to accommodate command line options that would normally be passed to the normal gksu application.

#!/bin/bash

if [ "$1" = "gksu" ] ; then
echo something > /usr/local/share/gksu-kill
shift
xterm -e su $1 -c "sudo rm /usr/local/share/gksu-kill"
  if [ -e /usr/local/share/gksu-kill ] ; then
  exit
  fi
  shift
  x=`grep "$@" /usr/local/share/gksu-list`
  if [ "$x" = "$@" ] ; then
    exec $@
  fi
  if `zenity --question --text "$@ is not in a trusted command, Should I add it"`
    echo "$@" >> /usr/local/share/gksu-list
    exec $@
  fi
exit
fi

---

### Post by quark_77 on 2007-04-30
Hi dagman,

Looks like you have a workaround... I've been sudoing everything and avoiding gksu or just not using fp authentication, whichever I feel like. I'll give your script a shot, thanks for the input!! Hopefully the gksu bug will be fixed sooner rather than later...

Quark_77

---

### Post by DagMan on 2007-04-30
I'll make it all a little clearer for other people and maybe someone will find a hole if there is still one, also I should have mentioned that the first one up top I found another security problem in which was just closing out the xterm.  In the one most directly above, I can't close out the xterm and if it were closed it still wouldn't allow execution of whatever's being passed to it.  I'll remove the original post actualy. I noticed a syntax error in the above one because I copied it from nano and part of one line was cut off.  I feel I should post the whole thing over again and state what the problems are... which I guess is that command line options to gksu screw things up so for example gksu -D /usr/bin/synaptic doesn't work.  Most things will work with the option removed but the more prudent thing to do would be to move the old gksu binary to another name, so 'mv /usr/bin/gksu /usr/bin/gksu2' for example and then it could be called for at the command line or in the launcher 'gksu2 -D /usr/bin/synaptic'

move the original 
```
sudo mv /usr/bin/gksu /usr/bin/gksu2
```

This following script gets named 'gksu' and can be put wherever it can execute from, mine's in /usr/local/bin

x=`echo $USER`
exec sudo access gksu $x $@
fi[/CODE]


The script access I stuck in /usr/local/bin

```

#!/bin/bash
if [ "$1" = "gksu" ] ; then
echo Something > /usr/local/share/gksu-kill
shift
xterm -e su $1 -c "sudo rm /usr/local/share/gksu-kill"
  if [ -e /usr/local/share/gksu-kill ] ; then
  exit
  fi
  shift
  x=`grep "$1" /usr/local/share/gksu-list`
  if [ "$x" = "$1" ] ; then
    exec $@
  fi
  if `zenity --question --text "$1 is not in a trusted command, Should I add it as trusted?"` ; then
    echo "$@" >> /usr/local/share/gksu-list
    exec $@
  fi
exit
fi
```

and the line added to the bottom of the sudo file which is accessed by typing 'sudo visudo'
```
ALL ALL = NOPASSWD: /usr/local/bin/access
```
for everyone in the group that can use sudo but like the following instead for just the user James
```
James ALL = NOPASSWD: /usr/local/bin/access
```
and in the sudoers file where the line that looks like this
```
Defaults        !lecture,tty_tickets,!fqdn
```
changed to this for to force authentication at every sudo
```
Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=0
```
but if a requthenticating every time isn't desireable then don't do that last line and instead of using the above 'access' script, use the following one instead
```
#!/bin/bash
if [ "$1" = "gksu" ] ; then
echo Something > /usr/local/share/gksu-kill
shift
xterm -e su $1 -c "sudo rm /usr/local/share/gksu-kill" 
  if [ -e /usr/local/share/gksu-kill ] ; then
  exit
  fi
  q=$1
  shift
  x=`grep "$1" /usr/local/share/gksu-list`
  if [ "$x" = "$1" ] ; then
    exec $@
  fi
  `zenity --info --text "$1 is not in a trusted command, try typing sudo echo $1 >> /usr/local/share/gksu-list to add it"`
  xterm -e su $q -c "sudo -k"
  su $q -c "sudo -k"
  sudo -k
exit
fi
```

... and hopefully in addition to finding bad holes, someone can add functions to handle all the possible command line options translating them from gksu to the sudo equivalent because I'm too lazy.

---

### Post by jckdnk111 on 2007-05-08
> **quark_77 said:**
> Even more fantastic than the first time, thinkfinger-0.3 is out, I've compiled & installed it and can now enroll users easier than on windows... no bioapi / pam_bioapi needed the software comes with all it needs ready, just a short compile!!

Thanks for all your links guys!!

Quark_77

How did you get in to compile? I've got libusb-dev and libusb-0.1-4 but I get a configure error saying libusb isn't installed?

Oh and I am running 7.04 (Feisty Fawn) ... any advice is greatly appreciated.

---

### Post by DagMan on 2007-05-09
I remember having to install some packages but don't remember specifially which ones.  I have these currently installed though:

libusb-0.1-4
libusb-dev
libusb++-0.1-4c2
libusb++-dev

---

### Post by jckdnk111 on 2007-05-09
hmmm .... I have the same packages installed but I still get the following error on configure:

...
checking for linux/uinput.h... yes
checking for pthread_create in -lpthread... yes
checking for pkg-config... no
checking for USB... configure: error: libusb missing

Do you (or anyone else) happen to know of a deb package available anywhere for version 0.3?
It might have the same problem I guess, but I can't seem to figure out why the libusb dependency is failing the check?

---

### Post by quark_77 on 2007-05-11
Hi All,

I had to install libusb-dev and libpam0g-dev and ran the configure script as follows:
```
./configure --with-securedir=/lib/security --enable-pam --with-birdir=dir=/etc/pam_thinkfinger --prefix=/usr
```
Which has just worked for me on Feisty as it did on edgy. I'm really not sure what to suggest in order to get this working... as I said this worked smoothly first time on my machine.

Have you built anything else that requires libusb?

Quark_77

---

### Post by jckdnk111 on 2007-05-11
> **quark_77 said:**
> Hi All,

I had to install libusb-dev and libpam0g-dev and ran the configure script as follows:
```
./configure --with-securedir=/lib/security --enable-pam --with-birdir=dir=/etc/pam_thinkfinger --prefix=/usr
```
Which has just worked for me on Feisty as it did on edgy. I'm really not sure what to suggest in order to get this working... as I said this worked smoothly first time on my machine.

Have you built anything else that requires libusb?

Quark_77

Well ... I never did get 0.3 to compile, but I found that my usb fingerprint reader isn't supprted on linux on Sony Vaio's anyways ([http://upek.mubeta.com/support/techsupport/faq/Topic.asp?ID_Topic=19](http://upek.mubeta.com/support/techsupport/faq/Topic.asp?ID_Topic=19)) 

Thanks for your help though.

---

### Post by alexsb on 2007-06-25
Hi,

I have exactly the same problems on my T61 ThinkPad - all the libusb libraries are installed but I still get the error message from ./configure. 

Any Ideas?

Alex

---

### Post by kansei on 2007-07-12
I just installed libpam0g-dev and libusb-dev and was on my way (on Ubuntu Gutsy Gibbon, freshly installed and updated).

I get right to the end of the install where I would enroll the user and bam it complains about not being able to find /etc/pam_thinkfinger

because yeah that doesn't exist. The only pam_thinkfinger on the system is in /lib/security as pam_thinkfinger.so

So I guess I havfe it built and installed but I definitely messed something up because it isn't looking in the right place when I run tf-tool

```
root@cdl-D620:~/Desktop/thinkfinger-0.3# tf-tool --add-user chris

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Could not access /etc/pam_thinkfinger: No such file or directory
root@cdl-D620:~/Desktop/thinkfinger-0.3# 


```

---

### Post by wladston on 2007-11-13
I'm having the same problem :(

---

### Post by wladston on 2007-11-14
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)

make sure you have apt-get instaled the 2 required packages.

---

### Post by adamvert on 2008-01-22
This worked perfectly - thanks!

---

### Post by [XAP]Bob on 2008-03-10
Added the repos from the Wiki, installed and enrolled myself.

For variety I'm running under Xen, and it seems mostly fine.

I rebooted and logged on without a hitch, then got presented with a gnome-keyring password prompt that did *NOT* take a fingerprint.

However my first gksudo program did ask for a password as normal (I was expecting it to display nothing as per the warning on the wiki) and then happily takes a fingerprint.

I'm really impressed - Although single swipe login (i.e. not requiring a username) would be nice I can live without it.

My one remaining issue (after my extensive 2 minutes of testing) is therefore the keyring prompt (which I only get if I login via fingerprint...)

---

### Post by [XAP]Bob on 2008-03-11
Actually - I looked more carefully at the workaround for using libpam-keyring, I hadn't got the "try_first_pass" option in the file, although the rest were already in place.

Added it and now I just swipe in (after typing my username)

Fabulous, and the only issue I can see with single swipe login is that my fingerprint is root as well (for kicks at the moment)

---

### Post by game_plan on 2008-04-28
I've installed all 3 packages listed in package manager in Hardy and I can get it to acquire and verify my fingerprint, but when I try to --add-user it says:
```

Could not access /usr/local/etc/pam_thinkfinger: Permission denied

```
So I tried creating that file, it stopped asking for it, but I don't know who to make the owner of the file, root and 16188 don't work

Please let me know who to make the owner, or what I need to do to be able to enroll fingerprints

---

### Post by game_plan on 2008-05-02
Is there really no one that can answer how to get this to work?

---

### Post by game_plan on 2008-05-05
Alright. I finally got this thing to work.

FOR ANYONE USING 64-BIT Hardy the 0.3 does not work as of now, the 0.2.2 seems to work fine. 

Hope that helps someone.

---

