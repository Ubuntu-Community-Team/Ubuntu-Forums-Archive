---
title: "All-caps directory names"
date: 2005-12-03
forum: General Help
---

### Post by WebDrake on 2005-12-03
Hello all,

I've been having a bizarre problem with some directory names on my Ubuntu system.  Namely: if I type mkdir DIRECTORY, with DIRECTORY in all caps, the name is automatically converted to lowercase.

This has happened, also, in cases where directories with all-caps names have been copied across from other locations.

What on earth is wrong here?  It's unbelievable to type, for example, mkdir JOE and then, with ls, to find the created directory is called joe; still more so when I can type, mkdir JOe, and that directory name will be respected.

:confused: 

Many thanks,

         -- Joe

---

### Post by soulestream on 2005-12-04
Per my understanding that is a function of Nautilis(and Konquerer) i believe, if you us e terminal it won't change case

soule

---

### Post by WebDrake on 2005-12-05
[QUOTE=soulestream]Per my understanding that is a function of Nautilis(and Konquerer) i believe, if you us e terminal it won't change case[/QUOTE]

Well, doing it in xterm still gets the same results... :-(

Is there any way to change the restriction?

I also get the following message if I type, e.g., "rename ran RAN" (ran being the directory name, and RAN what it's supposed to be):

'Bareword "ran" not allowed while "strict subs" in use at (eval 1) line 1.'

Any ideas?  I've not had this problem with other Linux systems I've worked on.

---

### Post by soulestream on 2005-12-05
the only thing i could find with that error with a little googling was perldata. 

Not really sure how that would effect bash, though


soule

---

### Post by WebDrake on 2005-12-06
After further checking I think there are actually two problems at work.  The "strict subs" error is indeed a Perl problem, to do with incorrect use of the rename function.  Here's what "man rename" has to say:

```

RENAME(1)              Perl Programmers Reference Guide              RENAME(1)

NAME
       rename - renames multiple files

SYNOPSIS
       rename [ -v ] [ -n ] [ -f ] perlexpr [ files ]

DESCRIPTION
       "rename" renames the filenames supplied according to the rule specified
       as the first argument.  The perlexpr argument is a Perl expression
       which is expected to modify the $_ string in Perl for at least some of
       the filenames specified.  If a given filename is not modified by the
       expression, it will not be renamed.  If no filenames are given on the
       command line, filenames will be read via standard input.

       For example, to rename all files matching "*.bak" to strip the exten&#8208;
       sion, you might say

               rename ’s/\.bak$//’ *.bak

       To translate uppercase names to lower, you’d use

               rename ’y/A-Z/a-z/’ *

OPTIONS
       -v, --verbose
               Verbose: print names of files successfully renamed.

       -n, --no-act
               No Action: show what files would have been renamed.

       -f, --force
               Force: overwrite existing files.

ENVIRONMENT
       No environment variables are used.

AUTHOR
       Larry Wall

SEE ALSO
       mv(1), perl(1)

DIAGNOSTICS
       If you give an invalid Perl expression you’ll get a syntax error.

BUGS
       The original "rename" did not check for the existence of target file&#8208;
       names, so had to be used with care.  I hope I’ve fixed that (Robin
       Barker).

perl v5.8.7                       2005-12-02                         RENAME(1)

```

However, the all-caps directory name problem appears to be something different in its own right.

For example, typing

           rename 'y/a-z/A-Z/' ran

gives an error message: "Can't rename ran RAN: File exists".

Again, working with xterm instead of gnome-terminal seems to make no difference....

:confused: 

Anyway, thanks for the advice. :-)

---

### Post by Liam on 2005-12-06
What happens when you do:

$ mv ran RAN

And can you make uppercase files, eg:

$ touch BLAH.txt

---

### Post by Liam on 2005-12-06
One more thing: what's your filesystem type?

Do a cat fstab and paste the line for the mount point of the directory you're working in.

---

### Post by Liam on 2005-12-06
Sorry, cat mtab, not cat fstab.

---

### Post by WebDrake on 2005-12-06
In this particular case I'm working on a FAT32 partition.

I have already tried the command "mv ran RAN", and I get the error: "File already exists."

I'm currently working under Windows so can't do the cat mtab command, but if it's important I'll come back later and do it. ;-)

---

### Post by mherring on 2005-12-06
Seems to be associated with FAT vs Linux file system type.  In a FAT directory, I found the same behaviour.  Further, I entered lc, then all caps---it would not accept the latter (file already exists)
DOS, Windows, FAT, etc.  not case-sensitive??

---

### Post by Liam on 2005-12-06
Depends on how it's mounted. Though if it's mounted explicitly as, say, DOS instead of vfat or auto in the fstab, I'd expect eight-character file names in all caps.

It might be worth doing the following:

$ sudo umount /your/fat32/mountpoint

Edit the line in the fstab for the mount point; change the third column to *vfat* if it's not already.

$ sudo mount /your/fat32/mount/point

---

### Post by WebDrake on 2005-12-06
It would appear to be a FAT32 problem; all-caps directories are fine on my ReiserFS home partition.

Here's the relevant line from the cat mtab statement:

```
/dev/hda5 /liquorboy vfat rw,nosuid,nodev,iocharset=utf8,umask=000 0 0
```

So, it's not that it's mounted as dos.

Oddly the system distinguishes partial-caps names, e.g. mkdir JOe results in---just that; it's only all-caps names that aren't applied.

---

