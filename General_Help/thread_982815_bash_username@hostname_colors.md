---
title: "bash username@hostname colors"
date: 2008-11-15
forum: General Help
---

### Post by arian40 on 2008-11-15
hey guys, i have read prob hole google and couldnt solve my problem, im new to linux (DESKTOP), and, im trying to make my username AND @ hostname on BASH colored so you can see the colors on SSH access (putty) too,
iv tried every thing nothing worked, oh btw, FOR ALL USERS, so i wont have to do each user one by one, to change their coloring,

here is my /etc/bash.bashrc 

```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
    ;;
*)
    ;;
esac

# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
	function command_not_found_handle {
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
		else
		   return 127
		fi
	}
fi
```

And here is My /etc/profile ( if you need it )

```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).


if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
   PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

```

I am using ubuntu latest version,
any help would be much appericated. thanx..

---

### Post by binbash on 2008-11-15
at .bashrc add at the end : 

PS1='[\u@\h \W]\$ '


BLUE=`tput setf 1`
GREEN=`tput setf 2`
CYAN=`tput setf 3`
RED=`tput setf 4`
MAGENTA=`tput setf 5`
YELLOW=`tput setf 6`
WHITE=`tput setf 7`
PS1='\[$GREEN\]\u@\h \[$BLUE\]\w/\[$GREEN\] \$\[$WHITE\] '

further read here : 

[http://wiki.archlinux.org/index.php/Color_Bash_Prompt](http://wiki.archlinux.org/index.php/Color_Bash_Prompt)

or 

[http://ubuntuforums.org/showthread.php?t=674446](http://ubuntuforums.org/showthread.php?t=674446)

---

### Post by arian40 on 2008-11-15
thanx so much, but just being abit extra, can you also make username and @ and hostname diffrent colors ? instead of all one color ?

---

### Post by jpkotta on 2008-11-16
```

# color escape codes
normal="\[\e[0m\]"
nobg="m\]"
blackbg=";40m\]"
redbg=";41m\]"
greenbg=";42m\]"
brownbg=";43m\]"
bluebg=";44m\]"
magentabg=";45m\]"
cyanbg=";46m\]"
greybg=";47m\]"
black="\[\e[0;30$nobg"
redfaint="\[\e[0;31$nobg"
greenfaint="\[\e[0;32$nobg"
brownfaint="\[\e[0;33$nobg"
bluefaint="\[\e[0;34$nobg"
magentafaint="\[\e[0;35$nobg"
cyanfaint="\[\e[0;36$nobg"
greyfaint="\[\e[0;37$nobg"
grey="\[\e[1;30$nobg"
red="\[\e[1;31$nobg"
green="\[\e[1;32$nobg"
yellow="\[\e[1;33$nobg"
blue="\[\e[1;34$nobg"
magenta="\[\e[1;35$nobg"
cyan="\[\e[1;36$nobg"
white="\[\e[1;37$nobg"
bold="\[\e[1$nobg"

# prompt pieces
prompt_open="$blue[$normal"
prompt_close="$blue]$normal"
prompt_close_open="$prompt_close$prompt_open"
prompt_username="$cyan\u$normal"
prompt_at="$blue@$normal"
prompt_hostname="$cyan\h$normal"
prompt_jobs="$cyan\j$normal"
prompt_time="$cyan\t$normal"
prompt_pwd="$magenta\w$normal"
prompt_cmd_num="$blue\#$normal"
prompt_err_stat="$bold$?$normal"
prompt_prompt="$blue\$$normal"

PLAIN_PROMPT='[\u@\h][\w](\j)\n\$ '
FANCY_PROMPT="$prompt_open$prompt_time$prompt_close_open$prompt_username$prompt_at$prompt_hostname$prompt_close_open$prompt_pwd$prompt_close_open$prompt_jobs$prompt_close\n$prompt_prompt "
export PS1=$FANCY_PROMPT

```

---

### Post by arian40 on 2008-11-16
should i replace the old one that this dude gave me with this one ?? or just add this extra code onto .bashrc ??

---

### Post by jpkotta on 2008-11-18
The snippets of code that I gave and that binbash gave are both stand alone.  Neither builds on the other.  If you add them both, the last one is the one that gets used.

I don't think I can make mine any clearer without recreating the documentation (which is [here]("http://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html"), btw).  Did you actually try it?  It's pretty obvious when you do...

---

### Post by SwordAngel on 2009-02-14
I'm not sure if this helps clarify the issue. For some reason, for the same Ubuntu box, if I connect to it from the command-line ssh client in Mac OS X Leopard, I automatically get green username@hostname; whereas I don't automatically get that colouring in PuTTY in Windows.

---

