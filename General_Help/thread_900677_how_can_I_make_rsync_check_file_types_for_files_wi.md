---
title: "how can I make rsync check file types for files without extensions?"
date: 2008-08-25
forum: General Help
---

### Post by pytheas22 on 2008-08-25
I'm using rsync to backup some files.  I only want it to backup files of certain types (.doc, .odt, .pdf and .txt).  I know that I can write regular expressions, put them in a file and use the --include-from= argument to tell rsync to copy only files whose names match that regular expression.

The problem with this is that, since I stopped using Windows, I got out of the habit of always adding extensions to file names (since Linux, unlike Windows, doesn't panic and have a fit if I try to open a file without a three-letter extension appended to its name).  I have a number of pdf's and text files in particular that don't have extensions on their names, so the regular expressions given to rsync wouldn't match them.

I guess I could write a bash script and use 'file' to pick out which file types to copy regardless of their extensions, but before I do that, I was wondering if anyone knew of an easier way to do this.  I thought rsync would have an argument that I could pass to tell it to figure out the file types on its own or something if they lack an extension, but I'm unable to find anything like that.

Thanks in advance for any suggestions.

---

### Post by unutbu on 2008-08-25
```

cd ~/Examples
find . -type f -print0 | xargs -0 file | grep -i ogg | cut -d ':' -f 1 | rsync -L --files-from - ~/Examples/ ~/Examples-0

```

Hi pytheas22, the above finds ogg files in ~/Examples, and copies them to ~/Examples-0.
Hope this helps.

---

### Post by pytheas22 on 2008-08-25
Thanks unutbu.  I modified that command a bit and it seems to work well:

```
find /home/chris/ -type f -print0 | xargs -0 file | grep -i -e ':.Microsoft Office Document' -e ':.*pdf ' -e ':.*odt ' | cfind /home/chris/ -type f -print0 | xargs -0 file | grep -i -e ':.Microsoft Office Document' -e ':.*pdf ' -e ':.*odt ' | cut -d ':' -f 1 >> rsync-dataut -d ':' -f 1 >> rsync-data
```

It matches all of the files I need and prints their paths into a text file, which I can then pass to rsync.

As a warning to anyone else who tries to do the same thing: I did have to edit the expressions that grep was matching a bit, because if you just use something simple like "grep -i 'doc'," you match not only Word documents but any files within a path containing 'doc'--so ~/Documents/picture.jpg would match, for instance.  That's why the expressions that I pass to grep are more specific.

Also, what would be really wonderful is if there were a way to tell rsync to transfer certain file types, regardless of extension, without having to use all this bash scripting--i.e., if there were a way to make rsync itself figure out file type other than looking at extensions.  If anyone knows how to do that, I'd love to hear it.

rsync knows how to do just about everything else, so I'd be surprised if the only way to select certain file types is to base it on extensions, which is a bad method on Unix systems.

---

