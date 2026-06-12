---
title: "[SOLVED] lm-sensors doesn't read sensors.conf file"
date: 2008-08-09
forum: General Help
---

### Post by impert on 2008-08-09
Hi all,
I've just updated my hardware, (mobo and CPU) and I'm having a problem getting the lm-sensors command **sensors - s** to work.

I've edited /etc/sensors.conf, and run **sudo sensors -s**, and rebooted, but when I run **sensors** I still get the raw data values and the label  and ignore commands don't work. In other words, **sensors** does not read or use the sensors.conf file.

However, if I run** sensors -c /etc/sensors.conf**, I get the right output.
Plain **sensors** and **sensors - c /dev/null** give the same results.  

I can't find anything  in [this thread]("http://http://ubuntuforums.org/showthread.php?t=2780"), or on the lm-sensors site, or in the etc/sensors.conf file which helps.

The new mobo is a Gigabyte GA-MA78GM-S2H with an ITE IT8718 chip. The CPU is an Athlon dual core 4850e. Incidentally, k8temp gives weird output, and there is no advice on tweaking it in /etc/sensors.conf.

Any ideas?

---

### Post by Vivaldi Gloria on 2008-08-09
> **impert said:**
> Any ideas?

I don't know much about sensors but why don't you try putting

```
alias sensors='sensors -c /etc/sensors.conf'
```

in your ~/.bashrc. Or you can try removing and reinstalling sensors.

---

### Post by FXEF on 2008-08-09
Go here for step by step instructions:
[URL="http://ubuntuforums.org/showthread.php?t=2780"]
http://ubuntuforums.org/showthread.php?t=2780[/URL]

Great HowTo!!

---

### Post by impert on 2008-08-10
Thanks for both replies. 
> 
I don't know much about sensors but why don't you try putting

Code:

alias sensors='sensors -c /etc/sensors.conf'

in your ~/.bashrc. Or you can try removing and reinstalling sensors. 

I've already removed and re-installed sensors.
I don't have a ~/.bashrc file. (Yes, I know it's a dot file). Should I make one?

> Go here for step by step instructions:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

Great HowTo!! 

Been there, done that. It's the link in my first post.


Could it be that there's a symlink missing? I looked for a link containing **sensors.conf** and there is none.

---

### Post by Vivaldi Gloria on 2008-08-10
> **impert said:**
> I don't have a ~/.bashrc file. (Yes, I know it's a dot file). Should I make one?

Are you sure that there is no .bashrc file in your home folder? Because the default ubuntu install comes with one.

Below is my .bashrc if you need it. It's the standard ubuntu .bashrc file except for the last three lines. Create a .bashrc in your home folder and paste the contents of my .bashrc in it. Add your alias for sensors at the end (see my post above). Save. Give the command

```
source ~/.bashrc
```

so that the changes take effect (or open a new terminal). Now try your alias.

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_colored_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    #alias ls='ls --color=auto'
    #alias saat='echo; date +%T" ("%Z")"; date -u +%T" ("%Z")"; date +%d" "%B" "%Y%t%n%A; echo'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi


export EDITOR=/usr/bin/nano
alias ls='ls -hF --group-directories-first --color=auto'
alias tym='echo; date +%T" ("%Z")"; echo; date -u +%T" ("%Z")"; echo; date +%d" "%B" "%Y%t%n%n%A;echo ;echo; cal -3'



```

---

### Post by impert on 2008-08-10
OOPS!

> Are you sure that there is no .bashrc file in your home folder? Because the default ubuntu install comes with one.

Of course there is. I don't know how I missed it before.   :oops:

I've done as you suggested and it worked like a charm. Thanks.
I'll listen to some Vivaldi to celebrate.

---

### Post by Vivaldi Gloria on 2008-08-10
> I've done as you suggested and it worked like a charm. Thanks.

You're welcome.

> I'll listen to some Vivaldi to celebrate.

:-)

---

