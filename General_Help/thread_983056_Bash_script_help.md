---
title: "Bash script help"
date: 2008-11-15
forum: General Help
---

### Post by f3tus on 2008-11-15
Okay, so here's the thing. I want to write a script that finds the name of a file with an .obj extension and then calls gcc to compile with that output name. For example file.obj: *gcc -o file file.obj*.

Now, I might mention I'm trying to do this with cygwin on XP, but the principle is basically the same, with one minor difference. The pipe key (|) does not work with non-American keyboards on the cygwin bash, so I have to use rxvt instead. Anyway, I get the filename without its extension with this (and yes, only one instance of an object file is expected):

```
rxvt -e ls -p *.obj | grep -v / | sed "s/\.[a-zA-Z0-9_-]*$//"
```

Now, I was thinking of storing this name to a string like:

```
string=`rxvt -e ls -p *.obj | grep -v / | sed "s/\.[a-zA-Z0-9_-]*$//"`
```

and then call gcc with:

```
gcc -o $string $string(could use * here as well).obj
```

But it isn't working...

Any thoughts?

Edit:
I don't need to call rxvt after all. Silly me. :)

---

