---
title: "[SOLVED] Calculate in Shell ?"
date: 2008-11-11
forum: General Help
---

### Post by sim-value on 2008-11-11
Hi ! 

Is there a way to do calculations in shell with entering for exampe echo 50+23 ?

Would be quite handy sometimes 

/me

---

### Post by roelpeeters on 2008-11-11
Hi,

What I did is I wrote a little perl script that transforms a string into a calculation and outputs the result. I use it like this:
```

pc '50+23'

```
And it will print the result: 73

The script is the following:

```

#!/usr/bin/perl
print eval(join(' ',@ARGV)).qq{
};

```

I saved it in my personal ~/bin directory which is in my path. Therefore I always have it available.

Roel.

---

### Post by geirha on 2008-11-11
The shell can only do integer arithmetics, so if you need to calculate with floating point numbers, you need to use an external command, like bc.

For integer arithmetics in the shell, you can use $((expression))
```
echo 50 + 23 = $((50 + 23))
a=50
b=23
echo $a + $b = $((a + b))
```

---

### Post by Sub101 on 2008-11-11
If you are talking about within a script you can use:

```
a=$(($b+$c))
```

Where a is your answer and b and c are two previously defined variables. If you know the numbers then

```
a=$((1+2))
``` would work just as well.

As for using this in the terminal. You can still use the $((1+2). It just gives you ```
bash: 3: command not found

```

which is the answer.

---

### Post by sim-value on 2008-11-11
Thanks to all of you !

---

### Post by doug1212 on 2008-11-11
How about this script for a calculator:

[HTML]http://www.novell.com/coolsolutions/tools/17043.html[/HTML]

---

