---
title: "Custom Bash Prompt Word Wrapping"
date: 2008-09-15
forum: General Help
---

### Post by tristicles on 2008-09-15
I know there are various threads about this, but none of them seem to answer my question. Being into eye-candy, I like to tweak the bash prompt. I want to add some colour and white space to make it easier to see where output of one command finishes and the next starts.

I've read about tweaking the PS1 string in ~/.bashrc. I'm aware of having to use \[\] to tell the terminal that the enclosed code is non-printing and ignore it when calculating screen width. Therefore, to make a blue prompt you'd do something like:

```
PS1='\[\033[1;34m\]\u@\h:\w $ \[\033[0m\]'
```

That works fine. As the current working directory gets so long, I'd like to have that on one line, the 'user@host' bit on a second line. This is where things go pear-shaped. Reading various guides about tweaking your prompt, you use \r and \n for new line and character return respectively.

Irrespective of if they're in [\ and \] or not, it just doesn't work for me. When the cursor reaches the end of the first line, it goes back to the beginning of the first line and over-types what I've put in. It's not 'til it gets to the second line that it goes down a line. Here's the PS1 from my ~/.bashrc.

```
PS1='${debian_chroot:+($debian_chroot)}\[\n\r\033[1;37;42m\] \w \[\033[0;m\n\r\033[1;37;45m\]\u@\h \[\033[1;33;44m\] \W \[\033[0m\]$ '
```

Not necessarily my final choice of colours. I'm just experimenting for the moment.
----------------------------------------------------------------------------
UPDATE (3-Aug-2009): Posted this initial problem whilst running hardy. Have since moved on to Intrepid and now Jaunty. Resolution is under Jaunty.

---

### Post by iponeverything on 2008-09-15
eek.. those are some scary colors.

i just truncate my path..

---

### Post by forger on 2008-09-15
For colouring, you also need grc
```
sudo apt-get install grc
echo "
#grc for colour output
if [ "$TERM" != dumb ] && [ -x /usr/bin/grc ] ; then
  alias cl='/usr/bin/grc -es --colour=auto'
  alias configure='cl ./configure'
  alias diff='cl diff'
  alias make='cl make'
  alias gcc='cl gcc'
  alias g++='cl g++'
  alias as='cl as'
  alias gas='cl gas'
  alias ld='cl ld'
  alias netstat='cl netstat'
  alias ping='cl ping'
  alias traceroute='cl /usr/sbin/traceroute'
  alias cat='cl cat'
  alias tail='cl tail'
  alias perl='cl perl'
  alias python='cl python'
fi" >> $HOME/.bashrc

```

Open a new terminal and check out an example:
```
cat /var/log/syslog
```

---

### Post by tristicles on 2008-09-18
Hi guys. Thanks for the response. Sorry about the delay in getting back. Life has this habit of getting in the way of things.

Good idea re truncating the path, iponeverything, but I like to know exactly where I am. Bit of a control freak!!! "Mist" could be /usr/share/icons/Mist or ~/.icons/Mist. Or do you mean you only keep the last x characters of the full path?

Forger, have installed grc and added that code to ~/.bashrc as suggested. /var/log/syslog certainly prints in pretty colours!! Didn't check it before the grc install. I had a coloured prompt before so I'm not too sure what functionality this has added. Must read up on grc. The problem with the prompt was the text wrapping. Unfortunately, this still remains (have closed the terminal and opened a fresh one since).

Hope this helps to clarify. If I need to type something with a long command line, say install a bunch of packages in one hit, I'd type something like this:

```

sudo apt-get install thunderbird gnomebaker compizconfig-settings-manager avant-window-navigator gparted isomaster smbfs medit

```

My current prompt looks like this:

```

[COLOR="Yellow"]~/Desktop[/COLOR]
[[COLOR="Blue"]user[/COLOR]@[COLOR="MediumTurquoise"]host[/COLOR]]$ 

```

Obviously it's on a dark background so looks better than that!!! When I enter the above command, this happens:

```

[COLOR="Yellow"]~/Desktop[/COLOR]
ig-settings-manager avant-window-navigator gparted isomaster smbfs meditf 

```

As you can see, the first line with the path in it has remained unchanged. The second line of the prompt with the first line of inputted code has been overwritten. Do I need to compensate for vertical space as well as horizontal with the PS1 syntax?

---

### Post by tristicles on 2009-08-02
Thought I'd blow the dust off this one!! Have found the problem. I'd ignored the "${debian_chroot:+($debian_chroot)}" bit at the beginning of the PS1 declaration. Not really sure what it does (will have a google for that in a bit) but it's obviously there for a reason!! Long commands are now wrapping on to a new line as required.

Have stuffed in a few variables to make it easier to read. Prompt now reads:
```

if [ "$color_prompt" = yes ];
then
    black="\[\033[0;30m\]"
    red="\[\033[0;31m\]"
    green="\[\033[0;32m\]"
    brown="\[\033[0;33m\]"
    blue="\[\033[0;34m\]"
    purple="\[\033[0;35m\]"
    cyan="\[\033[0;36m\]"
    lgrey="\[\033[0;37m\]"
    dgrey="\[\033[1;30m\]"
    lred="\[\033[1;31m\]"
    lgreen="\[\033[1;32m\]"
    yellow="\[\033[1;33m\]"
    lblue="\[\033[1;34m\]"
    lpurple="\[\033[1;35m\]"
    lcyan="\[\033[1;36m\]"
    white="\[\033[1;37m\]"
    PS1="${debian_chroot:+($debian_chroot)}\n${white}(${lgreen}\w${white})\n${lcyan}\u${white}@${yellow}\h${white}:$ "
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi

```

Hope this comes in useful for someone.

Kind regards from sunny blighty,
Tris

---

### Post by wodkaist on 2011-02-11
Met this issue too :

My line overlapped the first one when i type a big command.

Adding ${...chroot....} did not solved my problem.

The problem was about colors : I used syntax "\e[33;1m\]" for colors. Replacing them with variables like this solved my problem :


```
# Colors
black="\[\033[0;30m\]"
# ... See code below, from tristicles ...
white="\[\033[1;37m\]"

export PS1="${debian_chroot:+($debian_chroot)}\n${yellow}\w\n${lgreen}\u@\h${white}: "
```


Available on Github : [http://github.com/wodkaist/.home_shared](http://github.com/wodkaist/.home_shared)

---

