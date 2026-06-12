---
title: "variables"
date: 2008-09-03
forum: General Help
---

### Post by geezerone on 2008-09-03
I am looking for straighforward information on setting variables. I am not looking at complex applications but for now wish to set variables for various paths so making changing directories easier, e.g. rather than /home/myname/documents/music I can type cd $music.

TIA

---

### Post by pytheas22 on 2008-09-03
You can set bash variables with a command like:
```

music=/home/myname/documents/music
```

(There is no $ when you set the variable, although you need it when you access the variable, and there is no space on either side of the = sign.)

Then you could type 'cd $music' to cd to that directory.

Even better, you could set a variable like:

```
music='cd /home/myname/documents/music'
```

Then you could cd into the music directory by typing simply '$music,' without 'cd.'

If you want to apply the variable changes automatically in each shell every time you log in to a terminal, you have to edit your ~/.profile file.  [This page]("http://www.codecoffee.com/tipsforlinux/articles/030.html") has more details.

---

### Post by raptor2552 on 2008-09-03
Try using aliases. Open your .bash_aliases file in your home directory and put something like:

```
alias cdmusic='cd /home/myname/documents/music'
```

---

### Post by stylishpants on 2008-09-03
Using plain variables instead of aliases is often even more useful, guys.

It's more flexible.

It lets you do other things besides cd, such as 

```
mv *.mp3 $music
``` 

and 

```
find $music -iname \*"spice girls"\* 
```

without worrying about where your shell happens to be at the moment.

---

### Post by geezerone on 2008-09-04
Thanks for the replies folks. 

What would I need to add to the .profile file so that the variable is saved for future logins?

---

### Post by pytheas22 on 2008-09-04
> What would I need to add to the .profile file so that the variable is saved for future logins? 

Just add the commands to set the variables, one per line (or separated by ; ) to the file.  There's probably already some stuff in your .profile; add your commands below it.

.profile is just a script that gets run each time you log in, so any commands you put in there will be applied to each bash shell session that you start.

---

### Post by geezerone on 2008-09-04
Here is my .profile config with the line added at the end but doesn't work:

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

music='cd /home/myname/documents/music'
```

---

### Post by pytheas22 on 2008-09-04
Sorry, I told you to edit the wrong file.  You should edit ~/.bashrc instead.  I think that .profile is an older Unix convention, and if .bashrc exists, it gets used instead of .profile.

---

### Post by geezerone on 2008-09-04
Thanks for that it worked.

If you want to list the variables what is the echo command for that?

---

### Post by pytheas22 on 2008-09-04
> If you want to list the variables what is the echo command for that?

Is 'env' what you want?

---

### Post by geezerone on 2008-09-04
That doesn't output the variable I just configured. Is there a command to show all variables configured by user and default?

---

### Post by stylishpants on 2008-09-04
The "set" command, without any options, will display all shell variables and functions.

---

