---
title: "[SOLVED] using the shell for mass file manipulation"
date: 2008-08-26
forum: General Help
---

### Post by rossdub on 2008-08-26
I'm trying to move a large set of files in a large directory which meet certain criteria to a different directory.  I think that the easiest way to do this is with 'nested' functions on the command line.  Following some online tutorials and howtos, this is what I have have tried so far:

```
mv $(find . -name '*.m4p') /home/user/shared/DRMed/

```

but that returns this output:

```
mv: cannot stat /example.m4p no such file or directory
mv: cannot stat exmample/otherexample no such file or directory
 
```

I know that the 'find' portion of this works fine, it locates all of the correct files and lists them in 1 per line format.  The problem (I think) is in how mv parses the output from the find command.  Perhaps there is a simple option for find that will allow mv to properly interpret the results?  (-print0 does not work). Am I missing something obvious?  Tried the man pages, but couldn't find anything about linking mv and find there...please help!

---

### Post by phidia on 2008-08-26
Maybe you want to sort through/have CLI select the files you want to move before you invoke the mv command? Take a look at man grep and man cat too.

---

### Post by rossdub on 2008-08-26
> **phidia said:**
> Maybe you want to sort through/have CLI select the files you want to move before you invoke the mv command? Take a look at man grep and man cat too.

I thought that's what the ```
$(find ...)
``` portion did.  It is my understanding that commands inside the $( ) are run in a subshell as part of a while-do sort of loop.

---

### Post by rossdub on 2008-08-27
Well it took me all day, but I finally figured it out.  In case anyone else has this problem, here is the code that worked for me:```
/shared/music$ find . -name '*.m4p' -print0 | xargs -0 /bin/mv -t /home/user/shared/DRMed/
```

Just to describe what happens....
[LIST=1]
[*]Find all files in the current directory with the .m4p extension
[*]Print a list of the output adding a /null character to the end of the line instead of a carriage return
[*]Pipe the results into xargs with /null appended again
[*]move all of the files in the list to the directory specified
[/LIST]

Hope it helps someone.

---

### Post by munkyeetr on 2008-08-27
**EDIT: Never mind, I see what I missed. DUH. :oops:**

---

### Post by rossdub on 2008-08-27
Yeah, I saw your original message in my email.  No worries. My heart sunk when I thought it could have been done so much easier!  But I'm glad to know that all of my work wasn't in vain.  

Just in case anyone else has the same thought, the problem with munkyeetr's original suggestion was that the *.m4p files were spread out in different directories and subdirectories under music/. The command```
mv *.mp4 /home/user/shared/DRMed/
``` would have only moved the *m4p files in the current directory.  So my only options were to use that command and repeat it as many times as the number of directories which contained any .m4p files (which wasn't really feasible given that there were over 200 individual .m4p files spread out in different subdirectories under the 40GB music/ directory) or to use some sort of combination of pipes (| for the newbies), nested functions (see my first post here), and redirects (>) to find all of the .m4p files by searching music/ recursively and moving them in a single command line entry.  I'm quite pleased with the results. Perhaps I'll do a quick howto...

For more information on the commands I used, please read the man pages for find & xargs.

---

