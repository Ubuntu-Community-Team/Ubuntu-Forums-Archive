---
title: "[SOLVED] Logitech G11/Logitech G15 keyboard extra keys"
date: 2008-10-13
forum: Hardware
---

### Post by waltons_pacman on 2008-10-13
here goes:
UBUNTU HARDY 8.04
-----------------
recently got a new computer system, and the Logitech G11 Keyboard is part of what i have set up. it does work, flawlessly i might add, save for the lack of the the G-keys. 
what i want to be able to do is assign the g(1-18) keys to some random combination of buttons, for use with gaming through wine and whatnot. also would like the functionality of the m(1-3) buttons, and the MR button.
none of the M(1-3) buttons or the MR button light up, except for when i run 'g15macro' which output is:
---------------------------
restoring codes
XTest disabled by configure: no devel package was found.  Using SendEvent instead.
---------------------------
the M1 button immediately lights up, and M(1-3) and MR are functional. do not know if the g(1-18). 
g15macro does not terminate, but hangs there, seeming to wait for input.

currently, System->Preferences->Keyboard layout tab set to "Logitech G15 extra keys via G15daemon"


thanks for any time anyone puts into this.
~pacman

---

### Post by waltons_pacman on 2008-10-20
hate to do it, but BUMP.
been a week, think it is warrented. if not, feel free to <growl> at me here.

---

### Post by Markstar on 2008-10-21
Have you taken a look at [this page]("https://help.ubuntu.com/community/LogitechG15")?

This way, the G11 works for my except the M-keys - I do hope there is a solution for that, though but I am new to Ubuntu myself. 

Cheers
  Markstar

---

### Post by waltons_pacman on 2008-10-22
Markstar, TY for the post, but I have tried that page, no real help.
g15macro does what i want and has support for the M1-3 and MR keys;
however I'm working on it loading itself without displaying the terminal at startup. will repost when I have more time to play.

*Note*
g15macro can be found here:
[https://launchpad.net/ubuntu/intrepid/+package/g15macro](https://launchpad.net/ubuntu/intrepid/+package/g15macro)

---

### Post by waltons_pacman on 2008-10-22
**Solution to logitech G11 and G15 keyboards:**
to get the thing working, [follow this Guide]("https://help.ubuntu.com/community/LogitechG15").

**Extra Keys:**
G1-18, M1-3, and MR button
get [g15macro]("http://sourceforge.net/project/showfiles.php?group_id=172261&package_id=196992") and untar it.
run the following in the terminal:

1) cd <directory that it extracted into>
2) ./configure

[INDENT]2a) if ./configure does not say:
```
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands

```
then you may need one or more of the following:
[INDENT](libusb-dev from the synaptic package manager),[libg15 (1.2.6),]("http://sourceforge.net/project/downloading.php?group_id=167869&use_mirror=internap&filename=libg15-1.2.6.tar.bz2&70565177") [libg15render (1.2)]("http://sourceforge.net/project/downloading.php?group_id=1674&use_mirror=superb-east&filename=libusb-0.9.3.tar.bz2&41820615"), [g15daemon (1.9.5.3)]("http://sourceforge.net/project/downloading.php?group_id=172261&use_mirror=voxel&filename=g15daemon-1.9.5.3.tar.bz2&15795657")[/INDENT][/INDENT]

3) make
4) sudo make install
5) g15macro

at this point the g1-18 keys should light up if they hadn't already, along with the macro buttons.
press MR to record, a set of keyboard combinations, then the G1-18 button you want to assign it to.

*NOTE* you can always change what you recorded the same way later.

**getting g15macro to run at startx:**
when you are done with this, go to System -> Preferences -> Sessions
under Startup Programs, click ADD.
	name:	 g15macro
	command: g15macro
	comment: Enables the logitech G15 (or G11) G1-18, M1-3, and MR buttons.

---

### Post by Markstar on 2008-10-22
Hey, 
when I run *./configure*, I get the following error:
> configure: error: "libg15daemon_client (or its devel package) not found. please install it" :(

I checked Synaptic Package manager and I definitely have the libg15daemon_client installed - just to make sure I even installed the dev version. Do you have any idea what could hold me back?

---

### Post by waltons_pacman on 2008-10-22
quick google brings this:
g15daemon_client is from the g15daemon devel package. if you install that, then it should compile fine.

---

### Post by Markstar on 2008-10-23
> **waltons_pacman said:**
> quick google brings this:
g15daemon_client is from the g15daemon devel package. if you install that, then it should compile fine.As I have written in my previous post, I have already installed that. :(

---

### Post by waltons_pacman on 2008-10-24
from a clean install of ubuntu:
first install libusb-dev via the synaptic package manager.
then, install the following (in order!) by untaring, and cd to the untared directory and running the following commands.
# ./configure 
# make
# sudo make install
[libg15 (1.2.6)]("http://sourceforge.net/project/downloading.php?group_id=167869&use_mirror=internap&filename=libg15-1.2.6.tar.bz2&70565177")
[libg15render (1.2)]("http://sourceforge.net/project/downloading.php?group_id=1674&use_mirror=superb-east&filename=libusb-0.9.3.tar.bz2&41820615")
[g15daemon (1.9.5.3)]("http://sourceforge.net/project/downloading.php?group_id=172261&use_mirror=voxel&filename=g15daemon-1.9.5.3.tar.bz2&15795657")
[g15macro (1.0.3)]("http://sourceforge.net/project/downloading.php?group_id=172261&use_mirror=superb-east&filename=g15macro-1.0.3.tar.bz2&71382703")

the above should cover all the required dependencies, and install g15macro
once g15macro is installed, refer to post number 5.

---

### Post by Markstar on 2008-10-24
> **waltons_pacman said:**
> from a clean install of ubuntu:
I apologise for my ignorance...but what if I don't have a clean install? Is it alright to simply uninstall the packages in Synaptic (I will try this as soon as possible)? Or do I have to do any special clean-up?

Thank you for your time!

---

### Post by waltons_pacman on 2008-10-24
> **Markstar said:**
> I apologise for my ignorance...but what if I don't have a clean install?

one of two things:
1) uninstall what you do have that is relavent to this operation. 
2) try to install anyways, and you will get the "PACKAGE_NAME_HERE is already the latest version. operation aborted message."

the "from a clean install of Ubuntu" means that without any previously installed packages, this was all i had to do to get it to work, which means this should be all you need to get it to work.

---

### Post by Markstar on 2008-10-26
Hi,
I have followed your steps and noticed that your links are not quite right (G15Render links to libusb). Here is the correct link:
[G15Render (1.2)]("http://downloads.sourceforge.net/g15tools/libg15render-1.2.tar.bz2?modtime=1167691930&big_mirror=0"). 

As a result, I installed this after libusb and before G15Deamon (where it told me I need G15Render), so is this the right order?
[libg15 (1.2.6)]("http://sourceforge.net/project/downloading.php?group_id=167869&use_mirror=internap&filename=libg15-1.2.6.tar.bz2&70565177")
[libusb (0.9.3)]("http://sourceforge.net/project/downloading.php?group_id=1674&use_mirror=superb-east&filename=libusb-0.9.3.tar.bz2&41820615")
[G15Render (1.2)]("http://downloads.sourceforge.net/g15tools/libg15render-1.2.tar.bz2?modtime=1167691930&big_mirror=0")
[g15daemon (1.9.5.3)]("http://sourceforge.net/project/downloading.php?group_id=172261&use_mirror=voxel&filename=g15daemon-1.9.5.3.tar.bz2&15795657")
[g15macro (1.0.3)]("http://sourceforge.net/project/downloading.php?group_id=172261&use_mirror=superb-east&filename=g15macro-1.0.3.tar.bz2&71382703")


Anyways, I did not even get to the end. When I ran *sudo make install* while installing G15Daemon, I got this error:
```
In function ‘open’,
    inlined from ‘uf_conf_write’ at utility_funcs.c:359:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[2]: *** [utility_funcs.o] Error 1
make[2]: Leaving directory `/home/markstar/Progs/g15daemon-1.9.5.3/g15daemon'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/markstar/Progs/g15daemon-1.9.5.3'
make: *** [all] Error 2

```

I would start over, just to make sure, but I don't really know how (and where to delete the files I just installed. :redface:

---

### Post by Markstar on 2008-10-29
I tried some more to get this to work with no luck. 

I repeated the steps (but without removing the previous versions - I don't know how to do that), this time g15daemon gave me this at the end:
```
tribute warn_unused_result
utility_funcs.c:376: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
In function ‘open’,
    inlined from ‘uf_conf_write’ at utility_funcs.c:359:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [utility_funcs.o] Error 1
make[1]: Leaving directory `/home/markstar/Progs/g15daemon-1.9.5.3/g15daemon'
make: *** [install-recursive] Error 1

```I got no clue how to fix that, so I might just leave it be for now and be content with getting at least some shortcuts to work. 

I will try again tomorrow with a fresh install of 8.10.

---

### Post by melak on 2008-10-30
I'm getting the same issue as markstar on a clean install of ibex. Anyone know how to fix it?

---

### Post by cbt45 on 2008-11-01
It appears that the newer versions of gcc are more strict in the way the "open" function is called which is causing this problem on one line in the utility_funcs.c file.

To fix, go to line 359 in the file "<yoursrcdir>/g15daemon-1.9.5.3/g15daemon/utility_funcs.c" and change the following line:

config_fd = open(filename,O_CREAT|O_RDWR|O_TRUNC);

to

config_fd = open(filename,O_CREAT|O_RDWR|O_TRUNC,0664);

This will allow g15daemon to compile.

---

