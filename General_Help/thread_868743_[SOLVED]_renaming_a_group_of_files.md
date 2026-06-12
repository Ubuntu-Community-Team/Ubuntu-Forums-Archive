---
title: "[SOLVED] renaming a group of files"
date: 2008-07-24
forum: General Help
---

### Post by bilijoe on 2008-07-24
I periodically have a need to rename a directory of files, by prepending the date to the name.  I remember from my Unix days, I used to run a command something like this "mv * 72408*".     My memory must be faulty (surprise, surprise), because neither this, nor anything seemingly akin to it works.  I also have a [probably] one time need to add the ",jpg" extension to a directory of files which all simply have numeric names w/ no extension.  Again, [faulty]memory tells me that something like "mv * *.jpg" should work, but, of course, it doesn't.  

Can someone please help out this tired old brain of mine, and give me the correct command and syntax for both prepending a "tag" to a whole directory of files, and for adding an extension to a directory of files.  I'd be greatly appreciative.  I know, to you currently active Linux jocks out there, this will [probably] be child's play.  It's just that my memory is shot, and I've tried all the combinations and permutations of mv, cp, and rename I can come up with, and still I'm getting nowhere.:confused:

TIA,

---

### Post by vanadium on 2008-07-24
You probably will need "rename"

```

rename 's/^/72408/' *

```

---

### Post by bilijoe on 2008-07-24
> **vanadium said:**
> You probably will need "rename"

```

rename 's/^/72408/' *

``` How about dealing with adding the ".jpg" extension?

---

### Post by northern lights on 2008-07-24
Should you prefer a gui, xfce's file manager "Thunar" can be installed with an optional "Bulk Rename" package. It's in the repos.

---

### Post by vanadium on 2008-07-24
```

man rename

```

and probably a couple of tutorial sites on the web will help you to work with the rename command. Adding a .jpg extension can be achieved with

```

rename -n 's/$/.jpg/' *

```

Here I added the -n option, which shows how the files will be renamed without actually renaming them: good to test.

The * is the mask for the files on which to act. * means all files, but you can also use wildcard patterns to restrict the action to selected files, e.g. 2000* or *.png

---

### Post by mali2297 on 2008-07-24
Since *rename* isn't present in all Linux distributions, this alternative might be useful to know:
```

for foo in *; do mv $foo $foo.jpg; done

```

---

### Post by bilijoe on 2008-07-24
> **northern lights said:**
> Should you prefer a gui, xfce's file manager "Thunar" can be installed with an optional "Bulk Rename" package. It's in the repos. Actually, I'm an old command line hack.  Been at this since before the time when there even was a command line, let alone GUIs.  So I'm real comfortable w/ the command line approach.  Thanks for the info though.  It may still come in handy.

---

### Post by bilijoe on 2008-07-24
> **vanadium said:**
> ```

man rename

```and probably a couple of tutorial sites on the web will help you to work with the rename command. Adding a .jpg extension can be achieved with

```

rename -n 's/$/.jpg/' *

```Here I added the -n option, which shows how the files will be renamed without actually renaming them: good to test.

The * is the mask for the files on which to act. * means all files, but you can also use wildcard patterns to restrict the action to selected files, e.g. 2000* or *.png I think my real problem with "rename" is syntax for the PERL expression.  I've played around with a lot of things, but never even cracked a book on PERL.

---

### Post by evets25 on 2008-07-24
mali's solution with the for loop should work, and IMHO it's a much more elegant way to do it. +1

---

