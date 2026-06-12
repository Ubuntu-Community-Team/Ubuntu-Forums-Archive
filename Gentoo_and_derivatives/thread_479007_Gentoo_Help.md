---
title: "Gentoo Help"
date: 2007-06-19
forum: Gentoo and derivatives
---

### Post by durrell on 2007-06-19
I posted this on the Gentoo forum but no one has replied several hours later so I figured I'd try my luck here.

Well I installed Gentoo a few days ago with Gnome as the default window manager..everything worked, but the screen wouldn't scroll..well it would, but it took so long to refresh that it was impossible to get anything done. I have an Nvidia card and everything I read pointed to installing the nvidia-driver package. Well I did that. But then I realized I have to have the X windows manager installed. I installed the x manager package and FINALLY got my screen to refresh like it's supposed to..only to run into more issues.

Gnome runs, but it hangs at start up and the screen that shows "Nautilus starting", etc. with Gnome on it just stays there, no desktop background loads. I can't right click on my desktop..it just does nothing. I also can't run the file browser. None of my "Places" or "System" apps will load. Only programs under the "Applications" tab will run. And they run fine. Also, it will not boot into Gnome. It boots into the command line and I have to "startx" everytime I reboot. The Gnome tutorial said to do:

```
rc-update add xdm default
```

But when I try that I get:

```
 * xdm already installed in runlevel 'default'; skipping
```

What am I missing here? Any help is GREATLY appreciated.

Thanks!

---

### Post by coffeecat on 2007-06-20
Reading your post I think you have several issues to deal with. The slow and incomplete loading of gnome I have no idea about at the moment, but let's deal with the business of the desktop not starting up automatically.

You need to edit /etc/rc.conf. I post my rc.conf below. Don't copy it without reading through it and comparing with your own. This file you need to understand and be able to edit yourself. Be aware that it is a Gentoo-specific one, as is the rc-update system. Other distros have other ways of doing what this file does.

```
# /etc/rc.conf: Global startup script configuration settings

# UNICODE specifies whether you want to have UNICODE support in the console.  
# If you set to yes, please make sure to set a UNICODE aware CONSOLEFONT and 
# KEYMAP in the /etc/conf.d/consolefont and /etc/conf.d/keymaps config files.

UNICODE="yes"

# Set EDITOR to your preferred editor.
# You may use something other than what is listed here.

EDITOR="/bin/nano"
#EDITOR="/usr/bin/vim"
#EDITOR="/usr/bin/emacs"

# DISPLAYMANAGER has moved to /etc/conf.d/xdm

# XSESSION is a new variable to control what window manager to start
# default with X if run with xdm, startx or xinit.  The default behavior
# is to look in /etc/X11/Sessions/ and run the script in matching the
# value that XSESSION is set to.  The support scripts are smart enough to
# look in all bin directories if it cant find a match in /etc/X11/Sessions/,
# so setting it to "enlightenment" can also work.  This is basically used
# as a way for the system admin to configure a default system wide WM,
# allthough it will work if the user export XSESSION in his .bash_profile, etc.
#
# NOTE:  1) this behaviour is overridden when a ~/.xinitrc exists, and startx
#           is called.
#        2) even if ~/.xsession exists, if XSESSION can be resolved, it will
#           be executed rather than ~/.xsession, else KDM breaks ...
#
# Defaults depending on what you install currently include:
#
# Gnome - will start gnome-session
# kde-<version> - will start startkde (look in /etc/X11/Sessions/)
# Xsession - will start a terminal and a few other nice apps

XSESSION="Gnome"
```Edit your rc.conf and then post back with more about this odd gnome behaviour. I can't promise I'll be able to help any more because my knowledge is limited. I've managed to get Gentoo running nicely but I'm still learning. :wink:

A few general points. Make sure you have all the documentation and have read it. Look for the handbook and the documentation listings page on the Gentoo website. The [Gentoo wiki]("http://gentoo-wiki.com/Main_Page") is useful but not official and is of variable quality. Gentoo is a do-it-yourself distro and demands much, much, much more from the user than Ubuntu. I notice you call yourself a Linux 'nub'. I mean this kindly but you may find Gentoo too much just yet. I didn't manage to make a successful Gentoo install Until I had been using Linux for over a year and even then it was a helluva steep learning curve. I don't want to put you off but I warn you - many pitfalls lie ahead. :wink:

How did you install Gentoo? From the Gentoo CD? From a stage 3 tarball using another distro? Somehow else? The default Gentoo CD install only gives you a cut-down version of gnome. Try 'emerge -pv gnome' from a root terminal and you'll see what I mean. I don't think this is the cause of gnome not running properly but it's worth bearing in mind.

**Edit;** Whoops! Almost left you in the lurch. As well as rc.conf, check /etc/conf.d/xdm. It's self-explanatory. Here's mine:

```
# Tell X to always start on VT7. Otherwise it autodetects the first available
# VT, which means it has to wait until all gettys are started so it doesn't suck
# up a VT that should have had a login prompt (very slow).
# If XSTATICVT is on, the login manager will start as soon as possible during
# the boot process. If you want X to dynamically start on the first unoccupied
# VT after all gettys have started and you are using xdm, also remove the "vt7"
# from /etc/X11/xdm/Xservers.
XSTATICVT="yes"

# What display manager do you use ?  [ xdm | gdm | kdm | entrance ]
# NOTE: If this is set in /etc/rc.conf, that setting will override this one.
DISPLAYMANAGER="gdm"
```And do 'emerge --search gdm' to make sure you've got gdm installed. If not, emerge it.

**Edit 2:** That's 2 dashes before search in emerge --search. Something wrong with the board's font - in my machine at least. :(

---

### Post by scxtt on 2007-06-20
your "rc-update add xdm default" output is probably the result of xdm already being in the default runlevel ... here's the output of an **ls -l** for my runlevels directory:
```
scxtt@gentoo [/etc/runlevels/default]
:> ll
total 0
lrwxrwxrwx 1 root root 17 May 29 21:36 local -> /etc/init.d/local
lrwxrwxrwx 1 root root 20 May 29 21:36 netmount -> /etc/init.d/netmount
lrwxrwxrwx 1 root root 19 May 31 18:44 postfix -> /etc/init.d/postfix
lrwxrwxrwx 1 root root 16 May 31 01:22 sshd -> /etc/init.d/sshd
lrwxrwxrwx 1 root root 21 May 30 02:47 syslog-ng -> /etc/init.d/syslog-ng
lrwxrwxrwx 1 root root 22 May 30 02:48 vixie-cron -> /etc/init.d/vixie-cron
lrwxrwxrwx 1 root root 15 Jun  1 03:50 xdm -> /etc/init.d/xdm
lrwxrwxrwx 1 root root 20 May 30 02:41 net.eth0 -> /etc/init.d/net.eth0
```you can do **rc-update show** or **rc-update show default** to give you a listing as well ...

---

### Post by Kelsin on 2007-06-28
Make sure you have the lo network interface (the local loopback one). Gnome can boot REALLY slow and have issues if it's not there. When you configured your network scripts it's possible to disable it. So before you startx into gnome just double check that ifconfig has lo listed.

---

### Post by coffeecat on 2007-06-29
> **Kelsin said:**
> Make sure you have the lo network interface (the local loopback one). Gnome can boot REALLY slow and have issues if it's not there. When you configured your network scripts it's possible to disable it. So before you startx into gnome just double check that ifconfig has lo listed.

Good idea, but I doubt the OP will any take notice. His/her [near-identical thread]("http://forums.gentoo.org/viewtopic-p-4110761.html") on Gentoo forums also attracted a helpful response but, just as with this thread, the OP has yet to offer the courtesy of replying. Subsequent posts on Gentoo forums show that he/she has re-installed and has managed to get the GUI working. 

**durrell**, two comments. 

You rarely need to re-install Gentoo. I'm sure you could have repaired your original installation. Even if a Gentoo installation is so broken that it won't boot up it can almost always be repaired by chrooting from a live CD.

Your not replying to give some feedback is more than a discourtesy to the four people who took the trouble to answer your request for help. It is also a discourtesy to the many people who read forums to find solutions to similar problems. A final 'this worked or didn't work' or 'I've done this' can be informative.

---

### Post by durrell on 2007-06-30
Easy there killer..I've been fixing it the past few days, haven't had time to check back in here.

I always make sure to thank those who help me, regardless of if it works or not.

I just haven't had time to check back in. Very sorry, didn't mean to offend anyone.

And yes, I have gotten it fully functioning..but I had help from another non-Linux related forum from some friends of mine. I really just went to the handbook to figure out many of my problems. Now I know (as you said) most installs can be fixed from the Live CD.

Thanks for the help guys.

---

### Post by coffeecat on 2007-07-01
I'm glad it's working. I hope you enjoy your foray into Gentoo.

Two tips which really ought to be must haves. Emerge gentoolkit and read up about revdep-rebuild. You're gonna need it! :wink:

Number 2 - if you haven't already done so, read up about elogs. /etc/make.conf.example is not a bad place to start. A lot of essential post-emerge information (the sort that scrolls by too quickly in the terminal) is in there. And to make them easier to read, you can emerge elogviewer, a nice GUI app.

Good luck!

---

### Post by durrell on 2007-07-01
Yeah..at the end of something I emerged the other day it was telling me to run revdep-rebuild, so I went ahead and did that. I've actually had to use it several times now.

I haven't heard about elogs, I'll check into that.

Thanks. :)

---

