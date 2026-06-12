---
title: "[SOLVED] Odd bash behaviour with character ranges ([a-z])"
date: 2008-08-15
forum: General Help
---

### Post by alexdd on 2008-08-15
Hello,

I'm seeing some odd behaviour with the bash shell under Ubuntu 8.04, specifically in relation to character ranges, eg ls [a-z].  The ranges don't seem to behave as they should.

Here is output from a shell session to demonstrate the issue:

<output>
$ mkdir test
$ cd test
$ touch a
$ touch b
$ touch A
$ touch B
$ ls [a-z]
a  A  b  B
$ ls [A-Z]
A  b  B
</output>

The first ls should only show lower case filenames.  The second ls should only show upper case filenames.  Actually, the second ls has a further anomaly in that it misses out the lower case a.

I cannot find any logic in this.

Can anyone verify this with their installations, and/or explain if this is normal?

Using the same version of bash on a FreeBSD system I see more correct, expected behaviour.  I also see correct behaviour with zsh under Ubuntu, so it seems directly connected with bash under Ubuntu.

<env>
$ echo $SHELL
/bin/bash
$ bash --version
GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu)
Copyright (C) 2007 Free Software Foundation, Inc.
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
$
</env>

Thanks,

Alex

---

### Post by olejorgen on 2008-08-15
This is probably related to your LOCALE.
Try: ```

LC_ALL=C ls [a-z]

```

EDIT:
And yes, I get the same behavior (on debian testing though) (with en_US.UTF-8 locale)

Setting LC_ALL fixes it here.

The reason, I guess, is that [a-z] means every character that lies between a and z lexiographically. If you sort a list, and you're american, you'll sort it like this: Adam, crap, gnome, Gtk, all -> all, Adam, crap, gnome, Gtk

---

### Post by alexdd on 2008-08-15
Indeed, that does seem to be the issue ( LC_ALL=C ; ls [a-z] )

Thanks a lot.  I will investigate why the locale seems to make a difference.

Cheers,

Alex..

---

### Post by ibuclaw on 2008-08-15
This variable isn't set on my machine, so I doubt it be with yours either.

If you want, you can post a bug report about this (although, check for an existing one first).

In the meantime, open up your .bashrc file
```
gedit ~/.bashrc
```
or your system bashrc file if you have multiple users
```
sudo gedit /etc/bash.bashrc
```
and add
```
export LC_ALL=C
```
At the bottom.

Regards
Iain

---

### Post by pauper on 2008-08-15
> 2.4 Using Character Lists

Within a character list, a range expression consists of two characters
separated by a hyphen. It matches any single character that sorts between the
two characters, using the locale's collating sequence and character set. For
example, in the default C locale, ‘[a-dx-z]’ is equivalent to ‘[abcdxyz]’.
[i]Many locales sort characters in dictionary order, and in these locales,
‘[a-dx-z]’ is typically not equivalent to ‘[abcdxyz]’; instead it might be
equivalent to ‘[aBbCcDdxXyYz]’, for example.[/i] To obtain the traditional
interpretation of bracket expressions, you can use the C locale by setting the
LC_ALL environment variable to the value ‘C’. 

[Source.](http://www.gnu.org/software/gawk/manual/gawk.html#Character-Lists)

---

