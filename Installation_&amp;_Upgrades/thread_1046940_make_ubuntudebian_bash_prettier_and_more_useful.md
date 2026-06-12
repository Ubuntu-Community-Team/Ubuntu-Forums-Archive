---
title: "make ubuntu/debian bash prettier and more useful"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by SkyLeach on 2009-01-21
Well boys and girls, ladies and gents, geeks and hax0r chix, let's talk about that honestly fugly ubuntu PS1 prompt and some annoying decisions made for us that the average power user and/or system admin doesn't really need or want...

When working on several systems with several open terminal windows, wouldn't it be nice if we had a quick and easy visual cue as to whether we are logged in as root or not?  I mean, sure it's a generally a bad idea to be logged in as root, but when working on system maintenance tasks nobody wants to be typing in sudo all the time, and sudo just doesn't work at all for redirection pipes.

So let's go about making the prompt a nice warning RED when we are logged in as root, and a pleasant yellow for when we are logged in as a normal user.  In addition, let's set up some system-wide color options for ls so that we get a visual cue for file types without having to do ls -l or ll and then look at the flags.  This saves us time and make us more productive, which is always a good thing!

before making these changes, go ahead and back up your bash.bashrc file:
```

sudo cp -v /etc/bash.bashrc /etc/bash.bashrc.ubuntu.orig

```This is a patch file from my bash.bashrc that enables fortunes for interactive shells, colorful ls, and bash_completion.  Save it to a patch file in your home directory by **selecting it all with your mouse**, going to a terminal and do the following:

```

cd ~
cat > bash.bashrc.patch

```middle click on the terminal window to paste the patch text, then type ctrl+d to close the stream.

After saving it, patch your bash.bashrc by typing the following:

```

cd /etc
sudo patch -p0 < ~/bash.bashrc.patch

```The end result should change a terminal that looks like this:
[IMG]http://www.skyleach.org/images/default_bashrc.png[/IMG]
into this:
[IMG]http://www.skyleach.org/images/colorful_bashrc.png[/IMG]

**PLEASE NOTE**: in the patch file I also enable a fortune by default.  You need fortune-mod installed for this to work (otherwise you will get an error).  To install it do the following:

```

apt-get install cookietool display-dhammapada fortune-mod fortunes fortunes-bofh-excuses fortunes-debian-hints fortunes-mario fortunes-min fortunes-off libfortune-perl

```You can of course omit anything you don't think you will need (like cookietool if you aren't going to manage fortunes, libfortune-perl if you aren't a perl developer, etc...)

If you are easy to offend then omit fortunes-off (offensive) and open up the patched bash.bashrc file and change fortune -ao to fortune -a (the -o flag means offensive fortunes as well).

If you speak other languages, you can add fortunes-<linguas code> to that install string.

the files:

/etc/bash.bashrc.patch
```
*** bash.bashrc.ubuntu.orig     2008-09-29 14:17:51.000000000 -0400
--- bash.bashrc 2009-01-21 19:48:52.000000000 -0500
***************
*** 3,10 ****
  # To enable the settings / commands in this file for login shells as well,
  # this file has to be sourced in /etc/profile.
  
  # If not running interactively, don't do anything
! [ -z "$PS1" ] && return
  
  # check the window size after each command and, if necessary,
  # update the values of LINES and COLUMNS.
--- 3,22 ----
  # To enable the settings / commands in this file for login shells as well,
  # this file has to be sourced in /etc/profile.
  
+ # MATT CHANGE: The gentoo bashrc has a much better shell detection routine.
+ # Test for an interactive shell.  There is no need to set anything
+ # past this point for scp and rcp, and it's important to refrain from
+ # outputting anything in those cases.
+ if [[ $- != *i* ]] ; then
+       # Shell is non-interactive.  Be done now!
+       return
+ else
+       #matt change - let's get a fortune in here :-)
+       /usr/games/fortune -ao
+ fi
+ #ubuntu's crappy detection commented out... - Matt
  # If not running interactively, don't do anything
! #[ -z "$PS1" ] && return
  
  # check the window size after each command and, if necessary,
  # update the values of LINES and COLUMNS.
***************
*** 15,22 ****
      debian_chroot=$(cat /etc/debian_chroot)
  fi
  
  # set a fancy prompt (non-color, overwrite the one in /etc/profile)
! PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
  
  # Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
  # If this is an xterm set the title to user@host:dir
--- 27,96 ----
      debian_chroot=$(cat /etc/debian_chroot)
  fi
  
+ #matt change: i'm getting rid of this pansy ubuntu ps1.  let's put a real one in from gentoo :-)
  # set a fancy prompt (non-color, overwrite the one in /etc/profile)
! #PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
! ## BEGIN CHANGES ADDED FROM GENTOO BASHRC ##
! # Enable history appending instead of overwriting.  #139609
! shopt -s histappend
! 
! # Change the window title of X terminals 
! case ${TERM} in
!       xterm*|rxvt*|Eterm|aterm|kterm|gnome*|interix)
!               PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME%%.*}:${PWD/$HOME/~}\007"'
!               ;;
!       screen)
!               PROMPT_COMMAND='echo -ne "\033_${USER}@${HOSTNAME%%.*}:${PWD/$HOME/~}\033\\"'
!               ;;
! esac
! 
! use_color=false
! 
! # Set colorful PS1 only on colorful terminals.
! # dircolors --print-database uses its own built-in database
! # instead of using /etc/DIR_COLORS.  Try to use the external file
! # first to take advantage of user additions.  Use internal bash
! # globbing instead of external grep binary.
! safe_term=${TERM//[^[:alnum:]]/?}   # sanitize TERM
! match_lhs=""
! [[ -f ~/.dir_colors   ]] && match_lhs="${match_lhs}$(<~/.dir_colors)"
! [[ -f /etc/DIR_COLORS ]] && match_lhs="${match_lhs}$(</etc/DIR_COLORS)"
! [[ -z ${match_lhs}    ]] \
!       && type -P dircolors >/dev/null \
!       && match_lhs=$(dircolors --print-database)
! [[ $'\n'${match_lhs} == *$'\n'"TERM "${safe_term}* ]] && use_color=true
! 
! if ${use_color} ; then
!       # Enable colors for ls, etc.  Prefer ~/.dir_colors #64489
!       if type -P dircolors >/dev/null ; then
!               if [[ -f ~/.dir_colors ]] ; then
!                       eval $(dircolors -b ~/.dir_colors)
!               elif [[ -f /etc/DIR_COLORS ]] ; then
!                       eval $(dircolors -b /etc/DIR_COLORS)
!               fi
!       fi
! 
!       if [[ ${EUID} == 0 ]] ; then
!               PS1='\[\033[01;31m\]\h\[\033[01;34m\] \W \$\[\033[00m\] '
!       else
!               PS1='\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \$\[\033[00m\] '
!       fi
! 
!       alias ls='ls --color=auto'
!       alias grep='grep --colour=auto'
! else
!       if [[ ${EUID} == 0 ]] ; then
!               # show root@ when we don't have colors
!               PS1='\u@\h \W \$ '
!       else
!               PS1='\u@\h \w \$ '
!       fi
! fi
! 
! # Try to keep environment pollution down, EPA loves us.
! unset use_color safe_term match_lhs
! 
! #matt change: end of stuff brought over from gentoo
  
  # Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
  # If this is an xterm set the title to user@host:dir
***************
*** 27,34 ****
  #*)
  #    ;;
  #esac
! 
  # enable bash completion in interactive shells
! #if [ -f /etc/bash_completion ]; then
! #    . /etc/bash_completion
! #fi
--- 101,129 ----
  #*)
  #    ;;
  #esac
! #Matt change: this is ubuntu's bash_completion stuff... keep it
  # enable bash completion in interactive shells
! if [ -f /etc/bash_completion ]; then
!     . /etc/bash_completion
! fi
! 
! # sudo hint
! if [ ! -e $HOME/.sudo_as_admin_successful ]; then
!     case " $(groups) " in *\ admin\ *)
!     if [ -x /usr/bin/sudo ]; then
!       cat <<-EOF
!       To run a command as administrator (user "root"), use "sudo <command>".
!       See "man sudo_root" for details.
!       
!       EOF
!     fi
!     esac
! fi
! 
! # if the command-not-found package is installed, use it
! if [ -x /usr/bin/command-not-found ]; then
!       function command_not_found_handle {
!                 /usr/bin/command-not-found $1
!                 return $?
!       }
! fi

```You are going to want a copy of DIR_COLORS that is not included with either Debian or Ubuntu.  I am very happy to share mine, so here ya go:

/etc/DIR_COLORS
```
# Configuration file for dircolors, a utility to help you set the
# LS_COLORS environment variable used by GNU ls with the --color option.

# Copyright (C) 1996, 1999-2008
# Free Software Foundation, Inc.
# Copying and distribution of this file, with or without modification,
# are permitted provided the copyright notice and this notice are preserved.

# The keywords COLOR, OPTIONS, and EIGHTBIT (honored by the
# slackware version of dircolors) are recognized but ignored.

# You can copy this file to .dir_colors in your $HOME directory to override
# the system defaults.

# Below, there should be one TERM entry for each termtype that is colorizable
TERM Eterm
TERM ansi
TERM color-xterm
TERM con132x25
TERM con132x30
TERM con132x43
TERM con132x60
TERM con80x25
TERM con80x28
TERM con80x30
TERM con80x43
TERM con80x50
TERM con80x60
TERM cons25
TERM console
TERM cygwin
TERM dtterm
TERM eterm-color
TERM gnome
TERM gnome-256color
TERM konsole
TERM kterm
TERM linux
TERM linux-c
TERM mach-color
TERM mlterm
TERM putty
TERM rxvt
TERM rxvt-cygwin
TERM rxvt-cygwin-native
TERM rxvt-unicode
TERM screen
TERM screen-256color
TERM screen-bce
TERM screen-w
TERM screen.linux
TERM vt100
TERM xterm
TERM xterm-16color
TERM xterm-256color
TERM xterm-88color
TERM xterm-color
TERM xterm-debian

# Below are the color init strings for the basic file types. A color init
# string consists of one or more of the following numeric codes:
# Attribute codes:
# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white
NORMAL 00       # global default, although everything should be something.
FILE 00         # normal file
DIR 01;34       # directory
LINK 01;36      # symbolic link.  (If you set this to 'target' instead of a
                # numerical value, the color is as for the file pointed to.)
FIFO 40;33      # pipe
SOCK 01;35      # socket
DOOR 01;35      # door
BLK 40;33;01    # block device driver
CHR 40;33;01    # character device driver
ORPHAN 01;05;37;41  # orphaned syminks
MISSING 01;05;37;41 # ... and the files they point to
SETUID 37;41    # file that is setuid (u+s)
SETGID 30;43    # file that is setgid (g+s)
STICKY_OTHER_WRITABLE 30;42 # dir that is sticky and other-writable (+t,o+w)
OTHER_WRITABLE 34;42 # dir that is other-writable (o+w) and not sticky
STICKY 37;44    # dir with the sticky bit set (+t) and not other-writable

# This is for files with execute permission:
EXEC 01;32

# List any file extensions like '.gz' or '.tar' that you would like ls
# to colorize below. Put the extension, a space, and the color init string.
# (and any comments you want to add after a '#')

# If you use DOS-style suffixes, you may want to uncomment the following:
#.cmd 01;32 # executables (bright green)
#.exe 01;32
#.com 01;32
#.btm 01;32
#.bat 01;32
# Or if you want to colorize scripts even if they do not have the
# executable bit actually set.
#.sh  01;32
#.csh 01;32

 # archives or compressed (bright red)
.tar 01;31
.tgz 01;31
.svgz 01;31
.arj 01;31
.taz 01;31
.lzh 01;31
.lzma 01;31
.zip 01;31
.z   01;31
.Z   01;31
.dz  01;31
.gz  01;31
.bz2 01;31
.bz  01;31
.tbz2 01;31
.tz  01;31
.deb 01;31
.rpm 01;31
.jar 01;31
.rar 01;31
.ace 01;31
.zoo 01;31
.cpio 01;31
.7z  01;31
.rz  01;31

# image formats
.jpg 01;35
.jpeg 01;35
.gif 01;35
.bmp 01;35
.pbm 01;35
.pgm 01;35
.ppm 01;35
.tga 01;35
.xbm 01;35
.xpm 01;35
.tif 01;35
.tiff 01;35
.png 01;35
.svg 01;35
.mng 01;35
.pcx 01;35
.mov 01;35
.mpg 01;35
.mpeg 01;35
.m2v 01;35
.mkv 01;35
.ogm 01;35
.mp4 01;35
.m4v 01;35
.mp4v 01;35
.vob 01;35
.qt  01;35
.nuv 01;35
.wmv 01;35
.asf 01;35
.rm  01;35
.rmvb 01;35
.flc 01;35
.avi 01;35
.fli 01;35
.gl 01;35
.dl 01;35
.xcf 01;35
.xwd 01;35
.yuv 01;35

# Document files
.pdf 00;32
.ps 00;32
.txt 00;32
.patch 00;32
.diff 00;32
.log 00;32
.tex 00;32
.doc 00;32

# audio formats
.aac 00;36
.au 00;36
.flac 00;36
.mid 00;36
.midi 00;36
.mka 00;36
.mp3 00;36
.mpc 00;36
.ogg 00;36
.ra 00;36
.wav 00;36

```**NOTE**: If you follow these instructions and nothing happens, check that your ~/.bashrc file is sourcing /etc/bash.bashrc.

my root .bashrc file:

```

www etc # cat ~/.bashrc
[ -f /etc/bash.bashrc ] && source /etc/bash.bashrc

```Have fun!

---

