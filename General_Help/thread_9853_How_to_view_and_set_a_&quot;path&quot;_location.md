---
title: "How to view and set a &quot;path&quot; location?"
date: 2005-01-02
forum: General Help
---

### Post by marcadams on 2005-01-02
HI;

I am trying to install some additional packages for JBuilder 2005, which need to know about the location of JDK. Although Borland has installed JDK, I don't think the location is in the PATH. 

I would be very grateful if someone could tell me:

- How to chek if it is in the PATH - I.e how to view all the locations currently set
- If it is not there, how to add it to the path.
(I have tried: <export PATH=$HOME/opt/Borland/JBuilder2005/jdk1.4/bin:$PATH> but it does not seem to work)

When I try to run the additional installation, I get the following error: "No Java virtual machine could be found from your PATH environment variable.  You must install a VM prior to running this program."

Many thanks
Marc

---

### Post by alainhenry on 2005-01-02
To view current path, type 
echo $PATH 
from a terminal (PATH will be different if you are root or a user)
To add files to PATH, if I remember well, you should modify the file 
.bash_profile 
located in your user (or root) home directory, by adding at some point something like:
PATH=$PATH:$HOME/bin
export PATH

Alain

---

### Post by alainhenry on 2005-01-02
I just tried what I suggested above, and it did not work.  However, I tried it from the prompt, and PATH=$PATH:$HOME/bin changes PATH variable.  What did I miss ?
Alain

---

### Post by tomchuk on 2005-01-02
~/.bash_profile is ony sourced from a login shell - try setting environmental variables in /etc/profile or ~/.bashrc which will be sourced from a non-login shell (X-terminal).

The real way to do this is to properly install a system-wide JDK following the instructions from [here](http://wiki.osuosl.org/display/DEV/Java+on+Debian) which is the proper way to set up Java on a Debian-based distro.

---

### Post by marcadams on 2005-01-02
Hi, thanks for all your help.

With your help I've solved my immediate problem, by logging on as root, setting the PATH variable, and then installing my packages. 

However, as soon as I close the root terminal, the PATH is reset - as expected.

Incase I need this at a later stage (and as a learning exercise), I have tried to update my profiles for this new location. Looking at the suggestion by tomchuck, I went to the web site and followed the instructions JUST to set the PATH variable. I.e. I updated the PATH variable in both /etc/profile and /home/$USER/.bash_profile (I do not have a /root/.profile).

Unfortunately, after a reboot the PATH seems uneffected!

I.E., I have added to ".bash_profile" the following:
export PATH="/opt/Borland/JBuilder2005/jdk1.4/bin"

but when I log into the user terminal, and type "echo $PATH", only the original PATH value is seen. The above addition is ignored?

Does anybody have any suggestions?

Thanks
Marc

---

### Post by tomchuk on 2005-01-02
You need to add:
```
export PATH=${PATH}:/opt/Borland/JBuilder2005/jdk1.4/bin
```
to your ~/.bashrc so that non-login shells are affected.

Always make sure that you **append** (or prepend) to the PATH instead of clobbering it like in the line you posted above.

---

### Post by marcadams on 2005-01-03
Thanks Tomchuck;

I've added your suggested line to ~/.bashrc and rebooted - it worked!!

I've been a Windows Programmer for the last 10 years, but over the last few weeks I've been investigating Linux. There is a lot to learn....

Could you briefly tell my the difference between the ~/.bashrc and .bash_profile files? You said the ~/.bashrc file is used in non-login shells. In layman's terms what does this actually mean - I.e. I Log on as a specific user, both files are located in ~/ , so why is one used, and one not?

Thanks for your patience,
Marc

---

### Post by tomchuk on 2005-01-03
A login shell is executed from the login program which is run when you login from a VT (Ctrl+Alt+F1-F6). Under the X desktop the terminals you use execute a non-login shell which, if your shell is bash will only look at .bashrc. The quick and dirty way to make changes is to just modify /etc/profile which will affect longin and non-login shells for all users.

---

### Post by alainhenry on 2005-01-03
Thanks for the explanation, tomchuk, all the pieces I had before can now fit together.  And I can add ~/bin to my PATH

---

### Post by marcadams on 2005-01-03
Thanks Tomchuk (sorry for spelling your name wrong in previous posts!) - your description helps a lot.

Cheers
Marc

---

### Post by Olli on 2005-01-03
[QUOTE=tomchuk]A login shell is executed from the login program which is run when you login from a VT (Ctrl+Alt+F1-F6). Under the X desktop the terminals you use execute a non-login shell which, if your shell is bash will only look at .bashrc. The quick and dirty way to make changes is to just modify /etc/profile which will affect longin and non-login shells for all users.[/QUOTE] 
Thanks for  my part, too. I have a thick Debian Bible plus a score of manuals for RedHat-based distros, and none of them could explain to me why modifying the default path in /etc/profile did not suffice for adding new directories in PATH while working under a graphical user interface. I made the same error as alainhenry: I modified my local .bash_profile (because PATH was defined in /etc/profile), and commanded thereafter . .bash_profile, only to find that I had to repeat this command every time I open the X console.

---

### Post by earobinson on 2005-01-06
i am adding /home/earobinson/.scripts: to my /etc/profile and i still cant "Alt+F2" and run the programs that i am trying to link to why?

my /etc/profile looks like this
```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

PATH="/home/earobinson/.scripts:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/usr/bin/X11:/usr/games"


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

export PATH

umask 022
```

---

### Post by earobinson on 2005-01-07
i am adding /home/earobinson/.scripts: to my /etc/profile and i still cant "Alt+F2" and run the programs that i am trying to link to why?

my /etc/profile looks like this
```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

PATH="/home/earobinson/.scripts:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/usr/bin/X11:/usr/games"


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

export PATH

umask 022
```

---

### Post by OleMorten on 2005-01-31
why isn't the PATH in my /etc/profile exported? 
The first line in this file says:
export PATH=${PATH}:/usr/local/bin:/home/olli/eclipse:.

if I then write echo $PATH in the console, the extension doesn't show up. I set the PATH variable in .bash_profile too, in a similar manner(PATH=${PATH}:....), which works fine. In what other places is the PATH variable set? Think this is very confusing areas of Linux for most newbies, been reading for days now.

Thanks,
Ole Morten

---

### Post by alainhenry on 2005-02-01
As mentioned in a previous message of this thread, 
> ~/.bash_profile is ony sourced from a login shell - try
> setting environmental variables in /etc/profile or
> ~/.bashrc which will be sourced from a non-login shell (X-terminal).

The reason why Linux is set up like that is also briefly discussed above, though it remains somewhat unclear for me.  

Alain

---

