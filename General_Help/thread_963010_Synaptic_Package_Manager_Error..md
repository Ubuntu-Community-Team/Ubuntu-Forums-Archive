---
title: "Synaptic Package Manager Error."
date: 2008-10-29
forum: General Help
---

### Post by rags01 on 2008-10-29
When I Launch The SPM (synaptic package mangager) I get the following error:

E: Type 'echo' is not known on line 64 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

Then, 2 Days Later I Couldn't Boot Into Ubuntu It Just Shifted To A Black Screen With An Error Message That Goes Something Like This:

(BusyBox)blah blah blah Built-in Shell Debian

Or Something Like That?

What should I do? Are the 2 problems connected?

I managed to get into Ubuntu by booting using a previous generic grub loader or something and I am posting this On Ubuntu Now.

---

### Post by rags01 on 2008-10-29
Help? Please?

---

### Post by plucky on 2008-10-30
> E: Type 'echo' is not known on line 64 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.



There is an incorrect line in your **sources.list** file in line 64.
You will have to edit the file and delete that line.
To do so open a terminal and ```
gksudo gedit /etc/apt/sources.list
```
and search for the line that contains "echo" and remove it.

If you are not sure what you are doing,again from a terminal ```
cat /etc/apt/sources.list
``` and copy and paste to the forums so we can see it.

> (BusyBox)blah blah blah Built-in Shell Debian

Not sure about this,but were there any updates to your system,or did you change anything in the startup menu or Grub menu?

Can you open a terminal and post the output of ```
cat /boot/grub/menu.lst
```

---

