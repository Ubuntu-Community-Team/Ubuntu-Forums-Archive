---
title: "[SOLVED] bulk extraction help"
date: 2008-07-10
forum: General Help
---

### Post by slugicide on 2008-07-10
Hi, I have a folder with hundreds of folders in it.  In each of those nested folders are .rar files which I need to unpack.  How do I do this the Linux way? 
Thanks!

---

### Post by ibutho on 2008-07-10
You could write a script that goes through all the folders and unrars all the rar files that are present.

---

### Post by slugicide on 2008-07-10
I could write a script, but...
I don't know how.  If you pointed me to a tutorial which would teach me in a reasonable amount of time, I'd give it a shot.  But, if learning to write a script is going to take, like, 10 times as long as it would to just unpack them by hand...  But, then, as they say, "give a man a fish..."

---

### Post by ibutho on 2008-07-10
I'm not very good at shell scripting either. You could try something like
```
find /some/path -name "*.rar" -exec unrar x {} \;
```

---

### Post by MasterXandrex on 2008-07-10
That actually should work perfectly, if the situation is how your describe it. Good one.


Xan

---

### Post by slugicide on 2008-07-10
That's awesome!  THanks!
So, if I want to baleet the .rar files, do I go:

```
find  some/path -name "*.rar" rmv
```

---

### Post by MasterXandrex on 2008-07-10
What I think you mean is delete and I believe that it would be

```

find /some/path -name "*.rar" -exec rm -f {} \;

```


Xan

---

### Post by slugicide on 2008-07-10
Yeah, delete.  Cool, I see that the command is rm, and not rmv.  I shoulda known that.  Also, I see that it needs the -force, uh, argument? option?  What I don't quite get is the ```
{} \;
``` part.  If you have a minute could you explain or send me to an explanation?  Thanks!

---

### Post by ibutho on 2008-07-10
To get a good explanation, take a look at the manual for find ("man find" in a terminal). A snippet from the manual
> 
-exec command ;
              Execute  command;  true if 0 status is returned.  All following arguments to find are taken to be arguments to the command until an argument consisting of `;' is
              encountered.  The string `{}' is replaced by the current file name being processed everywhere it occurs in the arguments to the command, not  just  in  arguments
              where  it  is  alone, as in some versions of find.  Both of these constructions might need to be escaped (with a `\') or quoted to protect them from expansion by
              the shell.  See the EXAMPLES section for examples of the use of the -exec option.  The specified command is run once for each matched file.  The command is  exe&#8208;
              cuted in the starting directory.   There are unavoidable security problems surrounding use of the -exec action; you should use the -execdir option instead.



---

### Post by MasterXandrex on 2008-07-11
In other words, the "{}" stands for the filename that find finds and the "\" is used to escape the ";" so it is used as part of the command and not as command line termination.

Xan

---

