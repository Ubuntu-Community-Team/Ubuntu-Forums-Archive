---
title: "[SOLVED] User permissions have strange owner entry 501"
date: 2008-10-02
forum: General Help
---

### Post by 73ckn797 on 2008-10-02
I had lost my owner permissions on a number of files and directories. This has occurred after booting into a PCLinuxOS system and using several files and creating one new directory. I found how to change the permissions so that I could again have control over moving and copying those files. Copying to another drive and system /home and to NTFS drive were not being allowed.

One thing I noticed was that the owner was neither root nor myself but number 501. Where could this have come from? Was it from being in the other system and copying those files into the Ubuntu /home?

---

### Post by bodhi.zazen on 2008-10-02
Users are known by the system by number, not name.

501 = the user ID form PCLinuxOS.

some distros use 1000 as the first user, others (usually the rpm ones) use 500.

To see your user ID :

```
id
```

To show ownership by number :

```
ls -n
```

The system translates # to names in /etc/passwd

```
cat /etc/passwd
```

If there is no user associated with a number, ls will fall back to a number, in your case, on Ubunut, 501

[http://unixhelp.ed.ac.uk/CGI/man-cgi?passwd+5](http://unixhelp.ed.ac.uk/CGI/man-cgi?passwd+5)

---

### Post by 73ckn797 on 2008-10-02
That was what I was thinking happened.

I used the command "sudo nautilus" which gave me root access to make the changes. Found it in another thread.

What would be a good command/information reference I can buy or download? I have seen a few books on Ubuntu and/or Linux at the local store but would like to get recommendations from those who have or use one. I am sure  it is not bedside reading!

Montana huh? I have always wanted to visit Montana. One day maybe I will.

---

### Post by bodhi.zazen on 2008-10-02
The best way to learn the command line is to use the command line :)

Learn to interpret the man pages.

[http://linuxcommand.org/](http://linuxcommand.org/)[URL="http://linuxcommand.com"]
[/URL]

---

### Post by 73ckn797 on 2008-10-02
> **bodhi.zazen said:**
> The best way to learn the command line is to use the command line :) [http://linuxcommand.org/](http://linuxcommand.org/)[URL="http://linuxcommand.com"]
[/URL]

Best way to learn to work on an automobile is to bust a few knuckles but you still need technical specifications.

The link will probably be enough. Maybe a quick reference page or similar when I cannot access the computer.

Thanks

---

### Post by bodhi.zazen on 2008-10-02
LOL

Technical specs are right in front of you ...

man <command>

ie

man man

---

