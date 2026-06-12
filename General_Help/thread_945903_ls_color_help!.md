---
title: "ls color help!"
date: 2008-10-12
forum: General Help
---

### Post by zer0_mah on 2008-10-12
Hi,

I wanted to enable ls colour on my server Ubuntu 8.10. I researched how to do it and it said 'alias ls="ls --color=auto' in .bashrc of my home directory '/home/user' But here is my problem. I don't have .bashrc on my home directory. I have only .bash_history in my home directory '/home/user'

So, I created .bashrc home directory and added the alias command in the .bashrc file. But there is no color when i use ls. 
```
$sudo vi .bashrc
$alias ls="ls --color=auto"
$ls
```

I also copied the .bashrc file from '/root/.bashrc' to my home directory. But the color still didn't show up for ls.
```

$sudo /root/.bash /home/user
$ls
```

Please help me out how to set 'ls --color' for 'ls'?
I am just newbie for Ubuntu and Unix. I went through some research as above and still couldn't solve my problem yet. 

Is it all right to create .bashrc under 'home/user' by using 'sudo vi /home/user/.bashrc'?

Thank you

---

### Post by Sam on 2008-10-12
Try to replace your .bashrc file with the default in /etc/skel.

---

### Post by bodhi.zazen on 2008-10-12
Once you have added an alias to .bashrc you need to use it. Either start a new shell or "source"

you can either 

```
source ~/.bashrc
```

Or , for the lazy, source can be shortened to a .

```
. ~/.bashrc
```

Note the space between . and ~/.bashrc

---

### Post by Mister.Vash on 2008-10-12
You can check and see if the alias is actually set by typing in alias
```

alias

```
If that produces no output, then you have not successfully set the alias

I noticed that you used sudo when creating the file and copying the file.  Take a look at the permissions and owner of the file and make sure that your user account can read them.  If they are owned by root you should change ownership so that they are owner by your user account.
```

sudo chown $USER:$USER ~/.bashrc

```

Also, just to verify, you do get color when you run the command by itself?
```
ls --color=auto
```

If that command does not show colors, then you probably do not have the LS_COLORS options set.  This is what ls uses to determine which files should have what color.  To see if this is set, you can do the following:
```

echo $LS_COLORS

```
If this is blank, then they haven't been set. If you see a large out of values and extensions, etc.  then it has been set.

---

### Post by zer0_mah on 2008-10-20
Thanks for the replies guys.

It works now.:popcorn:
```
$source ~/.bashrc
```
This fixed the problem.

Here is my tutorial to get color output of ls command
```
$cd ~
$vi ~/.bashrc
alias ls='ls -F --color=auto'
$source ~/.bashrc
$alias
alias ls='ls -F --color=auto'
```

Thanks in advance guys :)

---

### Post by alphaniner on 2008-10-20
> I am just newbie for Ubuntu and Unix.

A noob?  I refute it thus:

```
vi ~/.bashrc
```

---

### Post by zer0_mah on 2008-10-20
> **alphaniner said:**
> A noob?  I refute it thus:

```
vi ~/.bashrc
```
That's the power of using search option. :)

---

