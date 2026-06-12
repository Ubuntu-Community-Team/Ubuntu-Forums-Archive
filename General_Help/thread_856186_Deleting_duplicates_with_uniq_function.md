---
title: "Deleting duplicates with uniq function"
date: 2008-07-11
forum: General Help
---

### Post by primky on 2008-07-11
I want to delete all duplicate lines from .txt files with uniq.

I tried 
> sort < input.txt | uniq
But that also sorts everything, which I don't want to.

I tried
> uniq input.txt output.txt

But it doesn't remove duplicate lines.
Any help?

---

### Post by roelpeeters on 2008-07-11
Hi!

In my opinion with a simple perl script you can solve this problem. Try the following.
```

#! /usr/bin/perl -w

my %known = (); # keep an hash array of the lines of text already seen

while(<STDIN>) # while we can read from STDIN
{
    if(!$known{$_}) # if this line is not known yet
    {
	$known{$_} = $_; # add it to our hash
	print $_;        # and output the line
    }
}

```

Save this piece of script to your directory and make it executable.
```

chmod +x dup.pl

```

Then use it as follows:
```

cat myfile | dup.pl

```

Hope this helps!

Roel

---

### Post by MasterXandrex on 2008-07-11
Uniq removes all successive duplicates, if you want it to remove all duplicates and just leave the first instance, use

```

uniq **-u** input.txt output.txt

```


Xan

---

### Post by justleen on 2008-07-11
or if you like unreadable syntax, use sed :)
```

 sed -n 'G; s/\n/&&/; /^\([ -~]*\n\).*\n\1/d; s/\n//; h; P'  filein > fileout 
```

---

### Post by unoodles on 2008-07-11
here's a quick python script:


```
import sys
x = open(sys.argv[1],'r')
xr = x.read()
x.close()
xrs = xr.split("\n")
newl = []
for item in xrs:
    if item in newl:
        newl.append(item)
y = open(sys.argv[2],'w')
y.write(newl.join("\n")
y.close()
```

just type `python file1 file2`

---

### Post by MasterXandrex on 2008-07-11
Uniq will get what you want with a simple flag -- why are you all trying to pound a nail with a shotgun? :D


Xan

---

### Post by ghostdog74 on 2008-07-11
> **UbuntuUser3859 said:**
> Uniq removes all successive duplicates, if you want it to remove all duplicates and just leave the first instance, use

```

uniq **-u** input.txt output.txt

```


Xan

you will have to sort it for it to work

---

### Post by ghostdog74 on 2008-07-11
> **roelpeeters said:**
> Hi!

In my opinion with a simple perl script you can solve this problem. Try the following.

Roel

try this too
```

perldoc -q unique

```

---

### Post by ghostdog74 on 2008-07-11
> **unoodles said:**
> here's a quick python script:


```
import sys
x = open(sys.argv[1],'r')
xr = x.read()
x.close()
xrs = xr.split("\n")
newl = []
for item in xrs:
    if item in newl:
        newl.append(item)
y = open(sys.argv[2],'w')
y.write(newl.join("\n")
y.close()
```

just type `python file1 file2`

a shorter way is to use set
```

data=open("file").readlines()
for i in set(data):print i

```

---

### Post by roelpeeters on 2008-07-11
@UbuntuUser3859: It all depends on the requirements the TS has for eliminating the duplicates. He does not want to sort his data (input and output). So lets take some examples:

test
test 
abcd 
efgh

Then a simple **uniq -u** will eliminate the lines with the value 'test'. And your output looks like this:

abcd
efgh

Then lets take another example:

test
test
abcd
efgh
test

Then uniq -u will output the following:

abcd
efgh
test

In my opinion, The data has been changed, in that it is no longer in the original order plus it removed also all lines which have a duplicate value. My script keeps all values and in case there are duplicates, only the first occurrence is shown. But then again, it is all up to the original poster.

@ghostdog74: Thanks for the tip, I am new to perl (and python for that matter) and always willing to learn something new.

And to make it complete: this is simply awesome and shows the power of ubuntuforums: within one hour three different solutions have been presented to a problem!

Roel

---

### Post by MasterXandrex on 2008-07-11
I see, didn't realize that.


Thanks,

Xan

---

### Post by ghostdog74 on 2008-07-11
```

awk '!_[$0]++' file

```

---

### Post by ghostdog74 on 2008-07-11
> **roelpeeters said:**
> 
@ghostdog74: Thanks for the tip, I am new to perl (and python for that matter) and always willing to learn something new.

```

perl -ne 'print $_ if !$a{$_}++;' file

```

---

### Post by blackhawx on 2010-07-01
> **ghostdog74 said:**
> ```

perl -ne 'print $_ if !$a{$_}++;' file

```

Ghost, where do you write this code in ubuntu and how do you execute it.  I'm new to executing perl commands.

thanks!

---

