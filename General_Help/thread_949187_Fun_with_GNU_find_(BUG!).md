---
title: "Fun with GNU find (BUG!)"
date: 2008-10-15
forum: General Help
---

### Post by pingnak on 2008-10-15
So, anyways, the 'find . -name' command his chosen this afternoon to BETRAY me by becoming partially blind to files.  When I tell it to find a name with a file glob, the results have become flaky.  It should be finding both the *.txt files, but it only finds one.  If I go down one folder and repeat it, I get both .txt files.  If I use -regex, I get both files.  

Here's the setup...
[B]mkdir test
cd test
mkdir blah
echo ME! > blah/findme.txt
echo FIND > findfind.txt
[/B]
**find**
.
./blah
./blah/findme.txt
./findfind.txt

**find -name *.txt**
./findfind.txt

**find -iname *.txt**
./findfind.txt

[B]cd ..
find test -name *.txt[/B]
test/blah/findme.txt
test/findfind.txt

But this works, so I have my work-around.
[B]cd test
find -regex ".*.txt"[/B]
./blah/findme.txt
./findfind.txt

**find --version**
GNU find version 4.2.32
Built using GNU gnulib version 8e128ebf42e16c8631f971a68f188c30962818be
Features enabled: D_TYPE O_NOFOLLOW(enabled) LEAF_OPTIMISATION 

I'm not exactly certain when this started choking.  I'm all patched up with the 'latest, greatest' stuff.

---

### Post by bingoUV on 2008-10-15
It has nothing to do with find. It is the way expressions evaluate in the shell, even before your command-line parameters reach find. Try this, maybe it will give you an understanding.
```

echo *

```

---

### Post by pingnak on 2008-10-16
What about it?  Are you saying it's a BASH bug?  A darned peculiar one, if so.  

Files aren't missing from the list when I type **ls -R**.

Find makes a recursive list of all files.

The -name parameter filters that list.  

The output of **find -name *.txt** should be identical to **find -regex .*.txt** in the test cases I gave.

It's not.  It's failing to operate predictably.

---

### Post by niteshifter on 2008-10-16
Hi,

It is not a bug, in bash or find. find is doing exactly what you (and bash) are asking it to do. Using the directory setup you gave and starting within the directory test:

```
find -name *.txt
```

The bash shell expands *.txt to an alpha sorted list of the _current working directory_ that match the pattern "<anything>.txt". So what find gets after bash is done is:
```
find -name findfind.txt
```
and there is a file by that name.

> Find makes a recursive list of all files.
Not quite:
> GNU find searches the **directory tree rooted at each given file name** by evaluating the given expression from left to right, according to the rules of precedence (see section OPERATORS), **until the outcome is known** (the left hand side is false for and operations, true for or), **at which point find moves on to the next file name.**

Having searched all - from ../../test downward - and finding only one file, which find printed to stdout (as specified), find is done.

---

### Post by bingoUV on 2008-10-16
> **pingnak said:**
> 
The output of **find -name *.txt** should be identical to **find -regex .*.txt** in the test cases I gave.

It's not.  It's failing to operate predictably.

niteshifter is right. Your regex "workaround" only works because it prevents shell from expanding *. In general, it is advisable to enclose * in quotes (") if you want the command to see * rather than expanded parameters by shell.

You failed to predict find's operation as you are unaware of bash regex expansion. Play around with shell to understand it better. echo is a good tool. For example, when you type **find -name *.txt**, if you want to see what find gets as input, do
```

echo find -name *.txt

```

What we are trying to say is, that find never saw the *. Find still thinks that you typed
```

find -name findfind.txt

```


And of course it is not bash bug. It is the intended behaviour, and quite useful at times.

---

