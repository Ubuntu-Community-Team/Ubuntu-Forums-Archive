---
title: "help writing script"
date: 2008-10-21
forum: General Help
---

### Post by Joshh100 on 2008-10-21
I'm trying to figure out how to write a script for ubuntu 8.04 that would automate the task of decompressing files that I download. For example, if I download ABC.zip or XYZ.rar or a tarball into a certain directory, I would like to run the proper program to decompress the file to a different directory. I mainly just want to do this to learn how to write scripts, but I'm not sure where to start. If someone could just point me in the right direction, I would greatly appreciate it.

---

### Post by hyper_ch on 2008-10-21
I'd say you

(1) need to read on cron
(2) learn howto use bash: [http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by tjwoosta on 2008-10-21
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

---

### Post by kpkeerthi on 2008-10-21
For zip support, you need unzip.
For rar support, you need unrar.

Both are available in the repositories.

---

### Post by Joshh100 on 2008-10-21
Thank you for pointing me in the right direction.. I already had those programs installed but I'll take a look at those links and see what I can come up with.

---

### Post by hyper_ch on 2008-10-21
and of course, another essential is the 
```

man

```
command.... commonly referred to as RTFM (which is not nice, yet it holds some truth).

The linux manual pages offer a very deep insight on how to run a certain command... some pages are easy to read, others more diffcult. Mostly you will also presented with a lot of examples on how to run a command.

So, if you want to find out how to use "unzip" on the command line, run
```

man unzip

```
Use arrow, pg up/donw keys to navigate and "q" to quit.

If you don't like that interface, you could also run
```

man unzip > ~/Deskop/unzip.txt

```
which will output the manual into that nice little text file on your desktop.

---

