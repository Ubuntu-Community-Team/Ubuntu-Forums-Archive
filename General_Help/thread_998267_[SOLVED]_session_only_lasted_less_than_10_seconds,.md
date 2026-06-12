---
title: "[SOLVED] session only lasted less than 10 seconds, et. al."
date: 2008-11-30
forum: General Help
---

### Post by scarf on 2008-11-30
help! ;) ubuntu-8.10 with all updates installed.

(this part may or may not be related, but is where i began to see problems).  i was trying to run audacity remotely thru ssh with x11 forwarding, with 'esd' and 'esddsp' to forward the sound also.  'esd' listening on my laptop, and 'esddsp' on the desktop to run audacity in the remote ssh session to connect to my laptop.  i got it working, but around the same time audacity began saying it could not create a temp file, permission denied, even tho i had specified a temp directory in my home dir with correct permissions.

back on the console of the desktop, i tried to run synaptic, just by clicking the icon from the administration menu, and i got this error:

unable to run /usr/sbin/synaptic as root
could not copy the user's Xauthorization file

i researched this error a bit and all i could find was to check the permissions on my ~/.Xauthority file, which i did, they are 600 (-rw-------), and owned by me.

if i log into the system remotely via ssh, i can use "sudo synaptic" and everything appears to work correctly, no visible errors, etc.

now i tried to reboot the system, and i can't log in!  it says:

"your session only lasted less than 10 seconds. if you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. try logging in with one of the failsafe sessions to see if you can fix this problem."

and this is my ~/.xsession-errors

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
mkdtemp: private socket dir: Permission denied

i researched this a bit and i checked my diskspace with df -h, everything is well away from 100% use.

i can log in using the failsafe GNOME session, but i do receive this error first:

there is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

---

### Post by scarf on 2008-12-01
here is some additional information that may help,

```

/etc/X11/xinit/xinput.d$ cat all_ALL 
#
# This configuration provides default IM setting (user edittable)
# See im-switch(8) and /usr/share/doc/im-switch/README.Debian .

#
# Define IM for traditional X application with XIM
#
#  XIM server name used for XMODIFIERS="@im=$XIM"
#  XIM program /path/filename
#  XIM program command line arguments
#
#  These were traditional setting before uim and scim for CJK languages
#  Language   LC_CTYPE     XIM server XMODIFIERS              Start key
#  Japanese   ja_JP*       kinput2    "@im=kinput2"           Shift-Space
#  Korean     ko_KR*       ami        "@im=Ami"               Shift-Space
#  Chinese(T) zh_TW.Big5   xcin       "@im=xcin-zh_TW.big5"   Ctrl-Space
#  Chinese(S) zh_CN.GB2312 xcin       "@im=xcin-zh_CN.GB2312" Ctrl-Space
# 
XIM=
XIM_PROGRAM=
XIM_ARGS=
XIM_PROGRAM_XTRA=
# Set following variable to non-zero string if program set itself as deamon
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=
#
# Define GTK and QT IM module
#   They may or may not be using xim as the IM.
#
GTK_IM_MODULE=
QT_IM_MODULE=

#
# Define lists of packages neded for above IM to function
#
DEPENDS=

#
# Define X start up hook script to update IM environment
#

/etc/X11/xinit/xinput.d$ 

```

---

### Post by scarf on 2008-12-01
oh, how wonderful!  i tried searching for "mkdtemp "private sock dir" "permission denied"" and it returned [_one hit_](http://www.linuxquestions.org/questions/debian-26/adding-a-regular-user-to-gnome-and-fluxbox-380631/).

the solution was to 'sudo chmod 1777 /tmp'

my /tmp permissions were only drwxr-xr-x

this has gotten rid of all errors, with audacity, synaptic, and i can now log in normally again without any errors.

i'm wondering though how the /tmp permissions got changed.  i would appreciate any insight.  do you think it is from the 'esddsp' program i was running? ....

---

