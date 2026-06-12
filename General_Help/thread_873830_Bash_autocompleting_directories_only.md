---
title: "Bash autocompleting directories only"
date: 2008-07-29
forum: General Help
---

### Post by beissemj on 2008-07-29
So I currently have a problem with bash autocompletion. Specifically it only autocompletes directories, and not files. This is not normal behavior in my opinion, as most other Distro's I've used if you press <tab> it will list all the directories AND files.

For example, if I want to edit fstab I have to manually type in the name, as bash will not autocomplete it.

Example
```
$ ls /etc/ | grep '^[Ff]'
fdmount.conf
firefox/
fonts/
foomatic/
fstab
fuse.conf

$ cd /etc/f<tab>
firefox/  fonts/    foomatic/

```

Also on another side note
```
$ cd ~/<tab>
(expands to)
$ cd /home/myuser/

```

Notice, that the directory gets explicitly expanded, which is a bit strange. Is this default behavior for bash in Ubuntu?

-M

EDIT: Maybe /etc/fstab is a bag example because of the permissions as sudo /etc/fstab will autocomplete, but even if I'm in my home directory I get the same only directory-completion.

---

### Post by geirha on 2008-07-29
Correction, for the cd command it only autocompletes direcotries. You can't cd to a file, right? 

```
gksu gedit /etc/f<tab> # should autocomplete fstab ...
ls /etc/f<tab> # same

```

EDIT: BTW, this behavior is configured in /etc/bash_completion and /etc/bash_completion.d/*

---

### Post by mali2297 on 2008-07-29
It is not special for Ubuntu, but a feature that you can enable in other distros as well.

I have this in my .bashrc file:
```

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
	. /etc/bash_completion
fi

```
You can disable the feature by commenting out these lines (also look in /etc/bash.bashrc).

However, I find it quite useful. For instance, since the command *cd* only accepts directory names as input, why would you want to see file names?

---

### Post by beissemj on 2008-07-29
In reality you wouldn't want to cd to a file, I just find it useful to see all the files in a directory with the cd command (force of habit more than anything).

As a side note I found the offending line for the cd command in /etc/bash_completion.

```

complete -d pushd

```

---

