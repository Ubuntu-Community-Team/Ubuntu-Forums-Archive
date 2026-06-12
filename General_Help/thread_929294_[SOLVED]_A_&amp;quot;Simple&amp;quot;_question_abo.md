---
title: "[SOLVED] A &amp;quot;Simple&amp;quot; question about Bash redirects"
date: 2008-09-24
forum: General Help
---

### Post by cryogen on 2008-09-24
Okay, this seems like a really silly question, but the answer is eluding me and so far google doesn't seem to have a clue either.

I'm trying to write a bash script that is called like this:

```
# ./myscript.sh < /path/to/some/file.ext
```

What the script needs to do is just echo back the file.  That is, the script should output:

```
file.ext
```

probably by using something like:

```
basename /path/to/some/file.ext
```

The problem I'm running into is that redirect.  I can't figure out how to read the file path and name into the script.  Bash stubbornly refuses to tell me what file it's reading from.  If I call the script like normal:

```
$ ./myscript.sh /path/to/some/file.ext
```

a simple:

```
basename $1
```

will do the job.  But the instant that redirect is in there everything breaks.

I don't care about the contents of the file (that's taken care of already), but I need name of the file that is being read from.

I know this is kind of a weird way of doing things, but I can't rewrite the method of calling since the script I'm trying to make is going to be called by an external program.  The filename is actually supposed to go into a search engine for the LAN and the spider reads things like this from stdout.

Any suggestions?  Is this even possible?

---

### Post by spibou on 2008-09-24
From [http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode)
> 
Typically, it is not possible to map from an open file to the filename that was used to open it. The operating system would convert the filename to an inode number at the first possible chance, then forget the filename.
This suggests to me that a Unix programme cannot find out the name of its stdin assuming the stdin comes from a disk file. So my guess is that what you're trying to do is impossible for reasons having to do with how the Unix/Linux filesystem is designed. But I could be wrong. I would suggest asking in a programming forum.

---

### Post by spibou on 2008-09-24
It occurs to me that the people at the kernel mailing list will definitely know whether Linux remembers the names of opened files or whether the name is forgotten and only the inode is remembered. But I don't know if they welcome such questions.

---

### Post by cryogen on 2008-09-24
Hmmm...  I'm thinking you're right.

After doing some more tests it doesn't appear that linux knows that information, probably for the reasons you state.

Bummer.  That complicates my project a lot.  Thanks for the help though.

---

### Post by cryogen on 2008-09-27
Update

I figured out that linux does indeed keep the information I was looking for.  Stupid me, I should have known: the files a process has open are listed as symbolic links in /proc/<pid>/fd  
](*,)

A shell script can tell what files it has open by using:

```
#!/bin/bash

varname=$$
ls -l /proc/$varname/fd
```

Or alternatively, a script can call lsof like this:

```
#!/bin/bash

varname=$$
lsof -p $varname
```

Just thought I'd post this here in case anyone else has this question.

Now I can actually finish my project!

---

