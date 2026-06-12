---
title: "Mass renaming files with no extension from cmd line"
date: 2008-09-02
forum: General Help
---

### Post by kreggz on 2008-09-02
Hello,

How do I rename files with no extension to .txt in the console? I would be doing about 150 at a time.

Cheers,

---

### Post by Jonie on 2008-09-02
```
for i in `ls`; do mv $i $i.txt; done
```

Do you think 150 at a time does require a special power? ;)

---

### Post by stylishpants on 2008-09-02
Here's one way to do it:
```
ruby -e 'ARGV.each {|f| next unless File.file?(f); next if f =~ /\./; File.rename(f, f+".txt") }' *
```

This will rename only plain files (not directories, symlinks, or devices) whose names do not contain a "." character.  It correctly handles filenames with spaces.  It examines every file in the current working directory.



The previous poster's code would rename every file and directory in the current working directory, except filenames with spaces, which it would choke on.
If you followed that advice, you may now have a directory full of files with names like "file.txt.txt" and "movie.avi.txt".  You could fix that problem by running this command: 

```
rename 's/\.txt$//' *
```

---

### Post by ghostdog74 on 2008-09-02
the most common way is to use find
```

find . -type f ! -name "*.*" -exec mv "{}" "{}"".txt"  \; 

```

---

### Post by kreggz on 2008-09-03
Thanks guys!

---

