---
title: "[SOLVED] Save cksfv output to text file"
date: 2008-08-04
forum: General Help
---

### Post by Vasto on 2008-08-04
Hello!
I'm trying to run cksfv on multiple directories and get it to save the output to a text file.
To run the cksfv check on multiple directories, I used the command
```
cksfv -r
```

Then after I realized I wanted it to save the data somewhere, I did:
```
cksfv -r > sfvcheck.txt
```

It created an empty text file, and nothing was being written to it.

Then after a bunch of searching, I found someone that suggested the below code for a slightly different case. I tried the code, but I have no idea where the output file would be/named.
```
cksfv -r 2>&1
```

Any help would be appreciated!

---

### Post by K2712 on 2008-08-04
> **Vasto said:**
> Hello!
Then after I realized I wanted it to save the data somewhere, I did:
```
cksfv -r > sfvcheck.txt
```

It created an empty text file, and nothing was being written to it.


That command should be correct to save the output to sfvcheck.txt.  This may be a dumb question but are you sure there are some .sfv files that exist in the directory/subdirectories you are in?

---

### Post by Vasto on 2008-08-04
> **K2712 said:**
> That command should be correct to save the output to sfvcheck.txt.  This may be a dumb question but are you sure there are some .sfv files that exist in the directory/subdirectories you are in?

Yes, because when I run
```
cksfv -r
```
it runs correctly and checks all the sfv files.

I'm confused as well as to why
```
cksfv -r > sfvcheck.txt
```
doesn't output to the text file, even though it displays in the terminal.

---

### Post by K2712 on 2008-08-04
I just tested it on my system and am having the same error.  I'll see what I can come up with, but hopefully someone else will know the answer....

---

### Post by Vasto on 2008-08-04
delete

---

### Post by Vasto on 2008-08-04
[QUOTE=http://zakalwe.fi/~shd/foss/cksfv/ChangeLog]
2007-03-25  Heikki Orsila <heikki.orsila@iki.fi>
	* Version 1.3.10
	- Added an option (-c) for remote programs to monitor sfv checking
	  more easily
[/quote]
I read the manpage and it doesn't even list a -c option. I also downloaded and compiled/installed the newest version. Still no text output.[/QUOTE]

---

### Post by derrick81787 on 2008-08-04
> **Vasto said:**
> Hello!
I'm trying to run cksfv on multiple directories and get it to save the output to a text file.
To run the cksfv check on multiple directories, I used the command
```
cksfv -r
```

Then after I realized I wanted it to save the data somewhere, I did:
```
cksfv -r > sfvcheck.txt
```

It created an empty text file, and nothing was being written to it.

Then after a bunch of searching, I found someone that suggested the below code for a slightly different case. I tried the code, but I have no idea where the output file would be/named.
```
cksfv -r 2>&1
```

Any help would be appreciated!

Try this:
```
cksfv -r > sfvcheck.txt 2>&1
```
Unix/Linux commands are supposed to send their output to stdout, but this one seems to use stderr instead.  stderr is represented as 2, and stdout is 1 but for convenience, you can leave it out. Basically "ls 1> out.txt" and "ls > out.txt" both redirect stdout to "out.txt" and "ls 2> out.txt" redirects stderr to "out.txt" (which would be empty in the case of ls). What the command above does is redirect stdout to "sfvcheck.txt" and redirect stderr to stdout, therefore both stderr and stdout will be in "sfvcheck.txt".  The following command would probably also work, but it only redirects stderr, so if something is actually printed to stdout, it wouldn't be in the file
```
cksfv -r 2> sfvcheck.txt
```

Basically, this command isn't behaving like most commands do, but it's output can still be redirected.

- Derrick

---

### Post by Vasto on 2008-08-04
> **derrick81787 said:**
> Try this:
```
**cksfv** -r > sfvcheck.txt 2>&1
```

Thanks a ton! I corrected the code just in case someone comes a long with the same problem. :-) I never knew what the 2>&1 thing did.


SOLVED!!

---

### Post by derrick81787 on 2008-08-04
> **Vasto said:**
> Thanks a ton! I corrected the code just in case someone comes a long with the same problem. :-) I never knew what the 2>&1 thing did.


SOLVED!!

Thanks. I edited my post to fix the typos.  You should mark this thread as solved by using the thread tools menu at the top of this thread. I'm glad I could help.

- Derrick

---

