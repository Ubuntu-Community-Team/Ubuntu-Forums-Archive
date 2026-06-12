---
title: "Strange bash related problem"
date: 2008-10-28
forum: General Help
---

### Post by ubtutu on 2008-10-28
I'm trying to get fifty random-ish bytes into a bash variable, but sometimes wc tells me I am getting 49. I need it to be 50 every time. What am I doing wrong? Thanks!!

```
user@machine:~$ fiftychars=`head -c 50 /dev/urandom`;echo -n $fiftychars | wc -c
50
user@machine:~$ fiftychars=`head -c 50 /dev/urandom`;echo -n $fiftychars | wc -c
49
user@machine:~$ fiftychars=`head -c 50 /dev/urandom`;echo -n $fiftychars | wc -c
50
user@machine:~$ fiftychars=`head -c 50 /dev/urandom`;echo -n $fiftychars | wc -c
50
user@machine:~$ fiftychars=`head -c 50 /dev/urandom`;echo -n $fiftychars | wc -c
50
user@machine:~$ fiftychars=`head -c 50 /dev/urandom`;echo -n $fiftychars | wc -c
50
user@machine:~$ fiftychars=`head -c 50 /dev/urandom`;echo -n $fiftychars | wc -c
50
user@machine:~$ fiftychars=`head -c 50 /dev/urandom`;echo -n $fiftychars | wc -c
50
user@machine:~$ fiftychars=`head -c 50 /dev/urandom`;echo -n $fiftychars | wc -c
49
user@machine:~$ fiftychars=`head -c 50 /dev/urandom`;echo -n $fiftychars | wc -c
50
```

---

### Post by geirha on 2008-10-28
You are getting a 0. Consider this:
```

$ threechars=`echo -en 'a\nb'`; echo -n $threechars | wc -c
3
$ threechars=`echo -en 'a\0b'`; echo -n $threechars | wc -c
2

```

---

### Post by caljohnsmith on 2008-10-28
I can't say for sure, but I'll bet your problem has something to do with the fact you are using /dev/urandom to generate the characters; maybe when urandom generates a space as the character for example, wc doesn't count it. Or something like that. :)

---

### Post by ubtutu on 2008-10-28
Thanks for the feedback guys, so how do I get around this issue?

I am guesssing that a zero not count as a character in wc, even though it is a character? Or is the problem with having zeros in bash variables?

My problem is that I dont know if the issue is with wc, or with bash variables. Am I to just trust that there are actually 50 bytes there even though I am unable to verify it with wc?

The below code confuses me..!

```
user@machine:~$ threezeros=`echo -en '\0\0\0'`; echo -n $threechars | wc -c
0
user@machine:~$ echo -en '\0\0\0' | wc -c
3

```

---

### Post by geirha on 2008-10-28
Well, you could use tr to translate \0 to something else

```
head -c 50 /dev/urandom | tr '\0' 'Z'
```

I'm fairly certain it's with bash variables. \0's just don't get stored.

---

### Post by ubtutu on 2008-10-28
Fixed, it seems the problem was with using bash variables.
If I redirect the randoms chars to a file instead of a bash variable, wc always reports 50 characters. Good enough for me!

---

