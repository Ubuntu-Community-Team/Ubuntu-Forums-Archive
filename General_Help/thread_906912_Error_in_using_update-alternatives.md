---
title: "Error in using update-alternatives"
date: 2008-08-31
forum: General Help
---

### Post by pauljoseph on 2008-08-31
Hi I am installing the latest octave 3.0.2 in Kubuntu 8.04. Since I am keeping the previous version, I thought it's better to use update-alternatives to manage. However, i got some error, can someone help to advise? 

```
$ sudo update-alternatives --install /usr/bin/octave octave /home/kurniawano/local/bin/octave 10
mv: cannot stat `octave': No such file or directory
update-alternatives: unable to rename octave to /usr/bin/octave: Invalid cross-device link
```

I checked the help it says the command is
--install <link> <name> <path> <priority>

in my case 
link=/usr/bin/octave
name=octave
path=~/local/bin/octave
priority=10 (this should be any integer right?)

I would appreciate your any advice. Thanks.

---

### Post by unutbu on 2008-08-31
What happens if you remove the symbolic link
```

sudo rm /etc/alternatives/octave
```

According to [http://www.mail-archive.com/debian-dpkg@lists.debian.org/msg02187.html](http://www.mail-archive.com/debian-dpkg@lists.debian.org/msg02187.html)
this quells the problem.

---

### Post by pauljoseph on 2008-09-01
Hi thanks for the prompt reply.
after I remove it and use the same command, it gives me this:

```
$ sudo update-alternatives --install /usr/bin/octave octave /home/kurniawano/local/bin/octave 10
mv: cannot overwrite non-directory `/usr/bin/octave' with directory `octave'
update-alternatives: unable to rename octave to /usr/bin/octave: Invalid cross-device link

```

---

