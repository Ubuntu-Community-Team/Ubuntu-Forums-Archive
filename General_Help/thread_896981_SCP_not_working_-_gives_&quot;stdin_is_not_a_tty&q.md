---
title: "SCP not working - gives &quot;stdin: is not a tty&quot;"
date: 2008-08-21
forum: General Help
---

### Post by becatlibra on 2008-08-21
I have googled this for a while and found inconclusive answers.  The general consensus is that if it works, who cares. . . 

This 'used' to work for me even with this message.  But now it does not function.

My syntax is simply

 scp filename [email]root@server.com[/email]:/home/user/

and then I get the error

 stdin: is not a tty

and nothing is copied.

Please help if you can.

---

### Post by HalPomeranz on 2008-08-21
I've seen this error when your ~/.profile or ~/.bashrc on the remote machine ("server.com" in your example) has a stty statement in it.  stty should only be used on interactive shells, and your scp session doesn't qualify.

The usual work-around is to prefix the stty statement with a conditional so that the stty is only executed in an interactive shell.  A typical idiom is:

```

[ "$PS1" ] && stty intr '^C' kill '^U' erase '^H' echoe

```

The stty command will only run if the first part of the expression above evaluates to true.  The environment variable $PS1 is only set if this is an interactive shell.

---

### Post by becatlibra on 2008-08-22
I had read this on the internet . . . I checked earlier both .bashrc and .bash_profile (and also /etc/bashrc and /etc/profile) and none of them have stty in them.

I am (for the hell of it) grepping the whole of both machines for the pattern stty - although I doubt this will help.  Any further suggestions from anyone?

Thanks

---

### Post by eldragon on 2008-08-22
maybe instead of allowing root to ssh, use a regular user :D

if you are trying to copy something inside the user's home do
```

scp filename user@server.com:path/inside/home_dir

```
it will copy to
```

/home/user/path/inside/home_dir/

```

---

### Post by HalPomeranz on 2008-08-22
> **becatlibra said:**
> I had read this on the internet . . . I checked earlier both .bashrc and .bash_profile (and also /etc/bashrc and /etc/profile) and none of them have stty in them.

I am (for the hell of it) grepping the whole of both machines for the pattern stty - although I doubt this will help.  Any further suggestions from anyone?


It could be another interactive command besides stty that's trying to execute from one of your start-up files and display output, etc.  You might try temporarily moving your start-up files on "server.com" out of the way and then doing the scp.  If the error goes away, you'll know that there's some issue with one of the start-up files.  Then add them back one-by-one until the error re-appears and you'll be able to narrow down the file that's causing the problem.

---

### Post by matey3 on 2009-01-21
I have this same problem and I think it is some sort of faulty installation of Ubuntu.
I have done all the updates etc, to no avail!

This is xen machine with problem, when I ssh to it as root I get the tty error and I have to close the terminal (I am using GUI) it freezes no ctl c out of.
When I go into the faulty machine and ssh to my workstation, I get a different error:

 ```
PRNG is not seeded
```

I dont know what PRNG is?
Any ideas?

---

### Post by matey3 on 2009-01-21
PARTIALLY SOLVED!

I got some ideas by looking here;
[http://lists.xensource.com/archives/html/xen-users/2006-09/msg00285.html](http://lists.xensource.com/archives/html/xen-users/2006-09/msg00285.html)

I used MAKEDEV under /dev to manually make those tty#s which did not exist? (why they weren't there? I dont know?) MAKEDEV tty1 or 0 or 2 whatever...
then I ran
 apt-get install udev
that updated all my c/cpp libs.
also as they suggested I put those 2 lines in my startup which the 2nd one was already there so I got a warning msg. 
update-rc.d -f udev start 03 S

Now I can ssh to it no problems and I am sure you can scp as well.
I am still having this error though at the boot up:
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console

this goes on until I break out of it?!

---

### Post by Peter_W on 2010-12-13
Hi, I had the same problem as the original poster and tried to solve the problem by putting

[ "$PS1" ] && stty intr '^C' kill '^U' erase '^H' echoe

into my .cshrc file (I'm using the C-Shell) after reading the first reply. This makes it possible to use scp to copy files to or from the account. However, upon log in I get the message "PS1: Undefined variable." and none of the other commands in my .cshrc file seem to be executed (aliases, setting up environment variables etc.). Is this because I'm using C-Shell rather than bash?

I've worked out that the offending stty command is in my .login file. Putting ["PS1"] in front of this command instead has the same effect.

How can I get scp to work whilst also getting the rest of my .cshrc file to load properly?

---

