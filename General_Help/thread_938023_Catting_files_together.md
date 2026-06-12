---
title: "Catting files together"
date: 2008-10-04
forum: General Help
---

### Post by SlaughterDog on 2008-10-04
This isn't so much a Ubuntu question as it is a unix question. I need help with the unix command *cat* (and maybe *split* if it's actually that one I'm using wrong).

So I want to just split a file apart and then cat it back together. I tried this in Ubuntu and I can't remember if I did it correctly or not. Now I tried this again in Damn Small Linux, and on Mac OS X. I don't know much about how things work in unix-like OSs, but it appears to me that when I cat the file back together, it loses it's type (if anyone could tell me how Linux and/or OS X know what type a file is, that would be great). The file I tried on DSL was an executable, and I could not get it to execute after I catted it back together. On OS X I split a tiff image, and after catting back together, Finder said it was a plain text file. I opened it with Preview and it opened fine. 

So how do I make it keep track of what kind the file is?

edit: also, with split, how do I make it append numbers to the end of the filename instead of letters?

---

### Post by jpkotta on 2008-10-04
There is no such thing as a file type in Linux or Windows.  IIRC, OS X does have some sort of metadata to identify the file at the filesystem level.  The only ways to "type" a file is to look at the data inside (generally what Linux does) or look at the filename (generally what Windows does).  Most filemanagers just look at the filename.

The file command will give you a guess as to what the file is.
```

$ file /bin/ls
/bin/ls: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
```
```

$ file /etc/fstab 
/etc/fstab: ASCII text

```

Use numerical suffixes:
```
split -d -b *size* *file* *prefix*
```

Concatenate files:
```
cat *prefix** > *concatenated_file*
```

Put a file extension on all files starting with *prefix*:
```
rename "s/$/.ext/" *prefix**
```

To learn more about how to use these tools, read the man pages:
```
man split
```

---

### Post by porchrat on 2008-10-04
> **SlaughterDog said:**
> 
edit: also, with split, how do I make it append numbers to the end of the filename instead of letters?

```
split -d [input [prefix]]
```

the "-d" option will give you numeric instead of letters.

You could also use "awk" to split the files up and then use "++" to add incremental numbers to the end of the file.

---

### Post by SlaughterDog on 2008-10-04
Thanks for the help, but that doesn't explain why on Linux, I couldn't launch that executable. I'm on the Mac right now, and I used the file command on the image file I split, and it said both of them were indeed tiff. Funny that Finder still shows the catted one as plain text, even with a .tif extension. I guess I'd have to post that one on a Mac forum then. (Oh, and the -d option doesn't seem to work on Mac, but I guess I could always rename them if I needed to).

I'm at work right now but when I get home I'll try this on Ubuntu. I still wonder why the file I tried on DSL wouldn't launch.

---

### Post by SlaughterDog on 2008-10-04
So I got back home an on Ubuntu I split a jpeg and catted it up. The file browser seemed to know just how to handle it. However, when I did a ls -F, I got this:
```
todd@computer:~/Desktop$ ls -F
[color=green]CocaCola.jpg[/color]*  test  x00  x01  x02  x03

```

So apparently there is something different. What's the color and * mean?

edit: Oh, figured out that it means it's executable.
So what are they other things? Monday on the mac at work I'll try to add x to the file at school and see if Finder treats it the same as the original.

edit again: Playing around, I have come to the conclusion that if you give a file a recognized extension, Nautilus will go by that, but if it has no extension, it will go by looking in to see what it really is, correct?

edit yet again: mmhm, catting files doesn't give execute to the file it creates. Explains why the game I tried last night didn't launch. 

Learning stuff like this is why I installed Ubuntu in the first place :D

---

