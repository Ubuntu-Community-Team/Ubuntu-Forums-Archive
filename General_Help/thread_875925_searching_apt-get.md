---
title: "searching apt-get"
date: 2008-07-31
forum: General Help
---

### Post by dgrafix on 2008-07-31
On fedora you can for example "yum search libxxx" and it will return a list containing that string. How to do this with apt? It only seems to work if you know the whole name which is sometimes annoying if its got something like: ".5.so.i386" or whatever on the end of it.

---

### Post by tamoneya on 2008-07-31
```
sudo apt-cache search package
```

---

### Post by Nepherte on 2008-07-31
You don't need sudo privileges to search:
```
apt-cache search <package name>
```
or
```
aptitude search <package name>
```

---

### Post by derrick81787 on 2008-07-31
> **Nepherte said:**
> You don't need sudo privileges to search:
```
apt-cache search <package name>
```
or
```
aptitude search <package name>
```

Both of these work even if you don't know the entire package name.  For example:

```
aptitude search abc
```

will return everything that has "abc" anywhere in the name.  I think that's what you're looking for.

- Derrick

---

### Post by unutbu on 2008-07-31
I think when you have a fragment of a filename and you want to find which package provides the file, the command you want is 
```

dpkg -S .5.so.i386
```
or
```
dpkg-query --search .5.so.i386
```
I have a hard time remembering all the different apt commands, so I wrote this little script to just try them all, one after the other:

```
#!/usr/bin/perl
use strict;
use warnings;

my $str=shift @ARGV;
my @cmd=("apt-cache search $str",
	 "dpkg --get-selections *$str*",
	 "dpkg -l | grep $str",
	 "dpkg -S $str",
	 "dpkg-query --list *$str*",
	 "dpkg-query --search *$str*",
	 "apt-file search $str",
);
my ($cmd,$resp);
foreach $cmd (@cmd) {
    print "$cmd\n? ([Y]/n/q) ";
    $resp=<STDIN>; chomp($resp);
    $resp='Y' if ($resp=~m/^\s*$/);
    if ($resp=~m/^y/i) {
	system($cmd);
    } elsif ($resp=~m/^q/i) {
	exit;
    }    
    print "\n";
}

```
Call it apt-search, make it executable:
```

chmod 755 apt-search
```
Use it like this:
```

apt-search .5.so.i386
```

---

### Post by caljohnsmith on 2008-07-31
Unutbu, in that perl script you wrote, you have:
```
dpkg --get-selections $str
```
I thought it would be worth mentioning that your statement will only find the package with the exact name of the value of $str. If you want $str to be a substring so that dpkg will return all package matches with $str in them, then you should put asterisks * around it, like:
```
john@TECH5321:/usr/local/bin$ dpkg --get-selections nautilus
nautilus					install
john@TECH5321:/usr/local/bin$ dpkg --get-selections *nautilus*
libnautilus-burn4				install
libnautilus-extension1				install
nautilus					install
nautilus-cd-burner				install
nautilus-data					install
nautilus-sendto					install
nautilus-share					install
```
I like your script though, it has about every combination of searching packages on the planet. :)

---

### Post by unutbu on 2008-07-31
Thanks caljohnsmith! I've updated the script.

---

### Post by dgrafix on 2008-08-01
Thanks guys!

---

