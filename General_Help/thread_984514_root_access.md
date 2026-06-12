---
title: "root access"
date: 2008-11-16
forum: General Help
---

### Post by swappo1 on 2008-11-16
Hello,

I have a question about root access.  I originally set my root access to have a password.  When I need to log in as root I type: > $su root I am then given a prompt for a password which I enter and gain access to root.  When done I type: > $su *username* I return to user access.  Earlier I accidentally typed > $sudo su I gained root access automatically with out having to enter my root password.  I might have been logged in as root earlier. How do I log out of root?  I know there is a time limit on root but I would still like to be able to log out when done.  Thanks

---

### Post by dwhitney67 on 2008-11-16
From a terminal, type in 'exit' to exit the shell.  I prefer not to type much, thus I enter ctrl-d.

Once you are logged in as root, using sudo is pointless.

Are you using Ubuntu?  It prefers to disable the root-account by not requesting the installer to assign a password.  This has its merits, but other distros still go along with the enabled root account.

P.S.  Running "su root" is the same as running "su".  Less typing... :-)

---

### Post by swappo1 on 2008-11-16
I tried exit and ctrl-d earlier but it just seems to change back to my user access while root is still active.  After I change back to user access if I type sudo su it automatically puts me right back into root access without asking for a password.  This leaves me to believe that I am not being logged out of root.  How would I completely log out of root where I would have to type my password again to log back in?

---

### Post by dwhitney67 on 2008-11-16
I have no idea how your system is setup, but typically when one is logged in as a regular user, the prompt has a $.  When logged in as root, the prompt should have a #.

I suspect that you are logging in as root, then continuing with a login as a regular user, and pretty much forgetting where you are at.

With the power of X11 and gnome (or kde), you are capable of opening multiple terminals.  Once you have finished your task in a terminal, close it, thus mitigating any problem of knowing whether you are logged in as root or a regular user.

---

### Post by swappo1 on 2008-11-16
When I open up a terminal I am at $.  When I log in as root I am at #.  When I su username, exit or ctrl-d while in root, I am back to $. If I close the terminal either by the x in the upper right of the terminal or by hitting ctr-d twice, after I open a new terminal, typing sudo su will take me back into root with the # prompt. Strange, I would think closing the terminal would also close the access to root.  Hmm.

---

### Post by Reiger on 2008-11-16
Your confusion probably stems from the fact that the terminal/sudo session keeps you logged on to sudo until you quit/exit that session. So, if you have done something like:

```

prometheus@Bartix:~$ sudo aptitude search foo
[sudo] password for prometheus:
p   bygfoot                         - soccer (football) manager game featuring t
i   foo2zjs                         - Support for printing to ZjStream-based pri
v   foo2zjs-ppds                    -
p   foobillard                      - a 3D billiards game using OpenGL
p   fookb-plainx                    - An Xkb state indicator -- plain X version.
p   fookb-wmaker                    - An Xkb state indicator -- WindowMaker vers
i   foomatic-db                     - OpenPrinting printer support - database
i   foomatic-db-engine              - OpenPrinting printer support - programs
i   foomatic-db-gutenprint          - OpenPrinting printer support - database fo
i   foomatic-db-hpijs               - OpenPrinting printer support - database fo
i   foomatic-filters                - OpenPrinting printer support - filters
p   foomatic-gui                    - GNOME interface for configuring the Foomat
p   libroxen-footnote               - Footnote module for the Roxen Challenger w
p   pysycache-move-food             - Food images for mouse move activities for
p   python-foomatic                 - Python interface to the Foomatic printer d
prometheus@Bartix:~$ sudo su
root@Bartix:/home/prometheus#

```

Note how at my first sudo call I'm prompted for a password but on the second call I'm not? That's got nothing to do with being logged on with su, but everything with sudo.

---

### Post by Bichromat on 2008-11-17
If you want to check whether 'root' is logged in, use
```
$ who
```

Like Reiger, I think what's happening here is that 'sudo' remembers your password from the last time you used it, and does not ask you again.

---

### Post by geirha on 2008-11-17
From the man-page of sudo:
```

       -k  The -k (kill) option to sudo invalidates the user&#8217;s timestamp by
           setting the time on it to the Epoch.  The next time sudo is run a
           password will be required.  This option does not require a password
           and was added to allow a user to revoke sudo permissions from a
           .logout file.

```

---

### Post by bapoumba on 2008-11-17
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

And moved to General Help.

---

