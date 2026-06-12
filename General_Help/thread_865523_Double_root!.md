---
title: "Double root?!"
date: 2008-07-20
forum: General Help
---

### Post by POW R TOC H on 2008-07-20
While doing something in the terminal, I acidently typed 
```
cd //
```
instead of
```
cd ..
```
To my great surprise, it worked. I was in // directory, which I never knew existed...
pwd returns '//' as well!
What's even weirder, using 'cd ..' when in '//' doesn't work (as you are in root) and the directory has the same files as '/'
Am I missing something here, or // really shouldn't exist :D ? 
I honestly never heard about it...

EDIT : Now I see that I can also go to // from nautilus. What is //? why and how does it work?

---

### Post by scragar on 2008-07-20
it's actualy exactly the same as / just under a different name, all the folders link to the same place etc, what's most intresting however is that /// automaticly redirects to / when // doesn't....

---

### Post by POW R TOC H on 2008-07-20
Yeah, I saw that too :)
But why does // exist, and where does it reside?
It has to be a real dir, otherwise it would not be shown as such with pwd.
If it is in root (which is the only place it could be, if you cd //), we should be able to see it with 'ls -a' if it was just a link :)

---

### Post by ymo on 2008-07-20
The // directory on Linux is just the / directory:
```
user@host:~$ cd //
user@host://$ pwd
//
user@host://$ /bin/pwd
/
user@host://$ cd ///
user@host:/$ pwd
/

```

Why do bash and other programs treat // differently to / and ///? Here is an answer Google turned up.> Jörg W Mittag:
The filesystem namespace beginning with '//' is reserved by POSIX as
an implementation defined namespace that is totally seperate from the
POSIX filesystem namespace beginning with '/'. "Implementation
defined" of course means, that any implementation can behave anyway it
likes in this namespace or -- to say it simple -- inside this
namespace you never know what's gonna happen. So, the behaviour of
Bash is neither right nor wrong, it's just what the Bash implementors
thought made sense. And I think they're right. Stripping one slash
would be wrong, because you cannot silently jump from one namespace to
another. However, doing something weird wouldn't be exactly helpful
either. So, pretending you were in the POSIX namespace but not
actually leaving the implementation defined namespace is exactly the
right thing to do.

In the "The Open Group Base Specifications Issue 6" at [http://www.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap04.html#tag_04_11](http://www.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap04.html#tag_04_11) you will find the statement:> A pathname that begins with two successive slashes may be interpreted in an implementation-defined manner, although more than two leading slashes shall be treated as a single slash.

Many years ago I used a computer system that used the // syntax to refer to files on another host:

//hostname/path/file

---

### Post by POW R TOC H on 2008-07-20
Thanks :)
That pretty much clears that up :) (somewhat)

---

