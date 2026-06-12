---
title: "Repair a .tar?"
date: 2008-10-15
forum: General Help
---

### Post by porchrat on 2008-10-15
Hello again.

Let me start by telling you the reason for this thread.  I wanted to know if anyone could recommend a utility for repairing archive files (.tar, .tar.gz, .tar.bz2 and .zip...they don't all necessarily need to be handled in the same tool).

I recently had some guidance from two extremely helpful and experienced individuals in creating a script to search through archive files.  See this post: [http://ubuntuforums.org/showthread.php?t=946280]("http://ubuntuforums.org/showthread.php?t=946280")

However I have since discovered that most of the archive files involved are corrupt.  (I suspect that tapes were copied to DVD's)

Incidentally some of the errors I get are as follows:

```
gzip: stdin: invalid compressed data--crc error
tar: Child returned status 1
tar: Error exit delayed from previous errors
```

```
tar: /directory/subdirectory/foo.tar: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now
```

Just in case those who like .zip files were feeling a little left out...don't worry, there are errors for the .zip files as well...

```
End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
```

Anyone have any recommendations?  I am completely stumped.

---

### Post by geirha on 2008-10-15
Run the file command on the problematic files. It will look inside the file and try to figure out what filetype it actually is. It may be a completely different type of file than a tar archive.
```
file /directory/subdirectory/foo.tar
```

---

### Post by porchrat on 2008-10-15
> **geirha said:**
> Run the file command on the problematic files. It will look inside the file and try to figure out what filetype it actually is. It may be a completely different type of file than a tar archive.
```
file /directory/subdirectory/foo.tar
```

Hello again :)

Have played around running "file" on random files within the group I'm looking through, problem is of course that the script I'm using doesn't tell me which archives are generating the error, so it is sort of luck-of-the-draw here.

Most .tar files come back with this:

```
POSIX tar archive (GNU)
```

---

### Post by porchrat on 2008-10-15
Sorry I see what you're saying...I will try that now.  I apologise for the slowness it has been a LOOONG day.

---

### Post by geirha on 2008-10-15
Try adding:

;file '{}'

behind the grep in exec.

---

### Post by porchrat on 2008-10-15
First one I tried comes back with this:


```
/directory/subdirectory/foo.zip: data
```

the tar errors don't ouput a filename, so I have no idea which .tar* archives are throwing those errors, however it comes back with quite a few ,zip archives that are creating problems

---

### Post by geirha on 2008-10-15
Hm, data means it's a binary file that the file command does not recognize. Try running strings on it. Not sure what you should expect, but it will print any sequences of ascii characters it finds in the file. Comparing it to another zip, it might give a clue of whether it has been a zip file once or not. I tried it on a random zip-file just now, and it printed alot of gibberish with some filenames inbetween that I recognized.

At any rate, it sounds like it is corrupt somehow.

---

### Post by porchrat on 2008-10-15
> **geirha said:**
> Hm, data means it's a binary file that the file command does not recognize. Try running strings on it. Not sure what you should expect, but it will print any sequences of ascii characters it finds in the file. Comparing it to another zip, it might give a clue of whether it has been a zip file once or not. I tried it on a random zip-file just now, and it printed alot of gibberish with some filenames inbetween that I recognized.

At any rate, it sounds like it is corrupt somehow.

OK ran a "strings" on it and got a whole lot of what looks similar to when you try to "cat" a compiled program...basically just garbled characters.  Unfortunately no filenames at all that I could recognise.  Also when I attempt to extract it I get his:

```
[/directory/subdirectory/foo.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /directory/subdirectory/foo.zip may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /directory/subdirectory/foo.zip or
          /directory/subdirectory/foo.zip.zip, and cannot find /directory/subdirectory/foo.zip.ZIP, period.

```

Looks like corruption to me :(

---

### Post by Dougie187 on 2008-10-15
May I ask where you got these tar and zip files that are corrupt?

---

### Post by porchrat on 2008-10-15
From a bunch of DVD and CD "backups" that, I'm starting to believe were taken from some old DAT tapes.  I'm not 100% certain (as the guy who made these backups is long gone), but I'm starting to get that feeling.

---

### Post by oldos2er on 2008-10-15
For *.zip files, try the command "zip -FF filename.zip".

---

### Post by porchrat on 2008-10-15
> **oldos2er said:**
> For *.zip files, try the command "zip -FF filename.zip".

Will give it a look in the morning, am not in fornt of the ubuntu machine at the moment.

---

### Post by porchrat on 2008-10-16
> **oldos2er said:**
> For *.zip files, try the command "zip -FF filename.zip".

OK gave it a go.  Didn't know that zip had a repair function, but I'm not surprised.  Unfortunately this is what it returned:

```
zip warning: foo.zip has been truncated.
foo.zip: adjusting offsets for a preamble of 8990077 bytes

zip error: Missing or empty zip file (foo.zip)
```

Anyone have any idea what can be done here?  If anything?  Is there any other way to attempt a repair?  Or are these things actually corrupted?

I don't have any experience with corrupted archives, so any advice or recommendations would be welcome.

---

### Post by porchrat on 2008-10-16
I can't find anything about this on google either...anyone ever been faced with this sort of scenario before?

Is there any way to determine whether or not the thing is corrupt, or if the indexes were lost or something?

---

