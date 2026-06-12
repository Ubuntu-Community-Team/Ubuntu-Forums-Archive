---
title: "mounting a NTFS partition's folder in /home?"
date: 2008-09-11
forum: General Help
---

### Post by milasch on 2008-09-11
I was wondering if it is possible to mount a NTFS partition's folder inside my /home partition.

For example, I want G:\Documents\My Pictures to become:

/home/milasch/Pictures

Is there any way to do that?

Or my best option would be to mount under /windows for example and create a link between /home/Pictures and /windows/Documents/My\ Pictures?

---

### Post by forger on 2008-09-11
You could mount it in /media/pictures and make a symbolic link at /home/username/pictures or wherever :)

```
$ ln --help
[...]
  -s, --symbolic              make symbolic links instead of hard links

```
symlink example:
[http://www.unixtutorial.org/2008/02/unix-symlink-example/](http://www.unixtutorial.org/2008/02/unix-symlink-example/)
[http://www.unixcommand.org/ln/](http://www.unixcommand.org/ln/)

---

### Post by mb_webguy on 2008-09-11
To expand on Forger's post...  

You mount a partition, not a directory.  You would have to mount the entire partition (which shows up as G:\ in Windows), and then create a link in your home directory to the My Pictures directory.

---

### Post by milasch on 2008-09-11
> **forger said:**
> You could mount it in /media/pictures and make a symbolic link at /home/username/pictures or wherever :)

```
$ ln --help
[...]
  -s, --symbolic              make symbolic links instead of hard links

```
symlink example:
[http://www.unixtutorial.org/2008/02/unix-symlink-example/](http://www.unixtutorial.org/2008/02/unix-symlink-example/)
[http://www.unixcommand.org/ln/](http://www.unixcommand.org/ln/)

Thanks!

What's the difference between symbolic links and hard links by the way?

---

### Post by forger on 2008-09-11
Searching in google gave me these:
[http://linuxgazette.net/105/pitcher.html](http://linuxgazette.net/105/pitcher.html)
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)
[http://wiki.answers.com/Q/What_is_the_difference_between_symbolic_link_and_hard_link](http://wiki.answers.com/Q/What_is_the_difference_between_symbolic_link_and_hard_link)

Enjoy reading :)

---

### Post by milasch on 2008-09-11
> **forger said:**
> Searching in google gave me these:
[http://linuxgazette.net/105/pitcher.html](http://linuxgazette.net/105/pitcher.html)
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)
[http://wiki.answers.com/Q/What_is_the_difference_between_symbolic_link_and_hard_link](http://wiki.answers.com/Q/What_is_the_difference_between_symbolic_link_and_hard_link)

Enjoy reading :)

errr... thanks

---

### Post by mb_webguy on 2008-09-11
> **milasch said:**
> Thanks!

What's the difference between symbolic links and hard links by the way?

A symbolic or soft link is like a shortcut in Windows.  It basically says "When someone looks here, send them over there".

A hard link is a bit like being in two places at once.  Instead of pointing to another place, a hard link makes it so that two (or more) paths map to the same storage location.

You should usually use symbolic links, since they're basically files redirecting you to another location and therefore easier to work with.  Some programs, though, aren't "fooled" by symbolic links and see them as just another file, which is why we have hard links.

---

### Post by Xeneth on 2011-06-14
Old post I know, and I do not know if it is the same as the answer OP has, but here's mine.

mount --bind

This will make what is saved in one directory be saved else-ware.  For  me, this was because my main storage was NTFS because it had to be  readable in my Windows 7.  So in /etc/fstab, I mounted the NTFS  partition as normal, done for me by Ubuntu 11.04:
```

# /windows was on /dev/sda3 during installation
UUID=FC843ED0843E8D60 /windows        ntfs    defaults,umask=007,gid=46 0      $

```Then I set the base storage folders to save their instead.

```

/windows/user/Documents/       /home/user/Documents/   none    bind  0  0
/windows/user/Downloads/       /home/user/Downloads/  none    bind  0  0
/windows/user/Pictures/        /home/user/Pictures/   none    bind  0  0
/windows/user/Videos/          /home/user/Videos/   none    bind  0  0
/windows/user/Music/           /home/user/Music/   none    bind  0  0



```This is all In /etc/fstab so it gets redone on boot.



Edit:  I posted because while I was searching for the answer, I got  here, and I wanted to make sure this post was useful to other's  searching.

---

### Post by WorMzy on 2011-06-14
But that's the wrong way around, Xeneth. In your example the files will be stored in your home folder, they'll just be accessible from /windows/shawn/* too. If the plan is to have files shared between Windows and Ubuntu, you'd need to have the files stored on the Windows partition, and then bind those folders onto your home folders.

---

### Post by Xeneth on 2011-06-14
yea, I noticed that.  Got ahead of myself when typing.  :)
Fixed now

---

