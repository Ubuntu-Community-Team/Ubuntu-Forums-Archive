---
title: "Help: Comparing Large and Massive Directories with Unmatched Names"
date: 2008-10-04
forum: General Help
---

### Post by dreikin on 2008-10-04
Over many years, and many computers, and many hard drives, I've amassed a quite large collection of _mostly_ redundant backups, most notably of music and image folders.  >=60 GB of stuff (for just the music!).  The same file may also not have the same name (eg, a 'full' name in one directory, and an 'iPod' name in another).  Diff'ing each file by hand would, of course, be a rather large pain, so anyone know a good utility for this?  (I'm searching the forums as well, but as mentioned in another post, there's a rather large amount of posts on diff'ing stuff, and this size of a project is prolly out of the norm).

Thanks

---

### Post by moshuptrail on 2008-10-04
I suspect what you want to do could probably be scripted, but you'll need to be more specific and provide an example or two.  It's hard to understand exactly what is needed from the description you've given.

---

### Post by dreikin on 2008-10-12
(bah - meant to get back to this sooner.  schoolschoolschool....)

Well, I've found a few things that come close to it, but still not a 'perfect' solution.

the program fdupes does pretty close to what I'm looking for (this is a description of how it does it, paraphrased from the man page):
[INDENT]1) Find all file in directories X and Y (-r for everything below them as well.

2) Sort all files by size.

3) In ascending or descending order, goto the first/next pair of files with the same size, until none remain.

4) md5sum those files and check if the sums match.
[INDENT]o If they don't, they're not the same, goto (3).
o If yes, then they might be the same, goto (5).
[/INDENT]
5) Compare files byte-wise
[INDENT]o If they match, print match and goto (3).
o If they don't match, just goto (3).
[/INDENT][/INDENT]

Which is pretty much what I'm looking for, but in diff as well (haven't found a method for that in diff's man or info yet).  Especially that it matches by size, not by name or location, as the files I'm working with have probably/often been renamed and/or resorted into directories, and I'm looking to find which ones are redundant and which ones aren't, for a LOT of files (before I started pruning, that was probably >100GB of music&pics, and is still probably >(several hundred thousand or a few million) pics (yes, I hoard them, but they're mostly small pic files, not 5MP+ digital-camera-quality - though there are some of those as well to be checked).

*(However, sometimes they've been reripped, so I'd like a directory-structure agnostic comparison by file names as well, but I'm not quite at that stage yet...)*

Thanks for the response though!

---

