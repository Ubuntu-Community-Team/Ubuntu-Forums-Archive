---
title: "[SOLVED] Not sure if what I discovered is a bug"
date: 2008-11-21
forum: General Help
---

### Post by ItsJweed on 2008-11-21
I'm not sure if what I discovered is a bug, or simply arises because I'm attempting to do something that I shouldn't be trying to do. Here is what happens:

Type at the terminal:

cat /dev/urandom

Let this execute for several seconds and then press ctrl-c. If the terminal prompt reappears as normal, try the above command a few more times. What I have discovered is that everything I type into the terminal after that command appears as garbage. It seems the commands execute, but it's impossible to tell what is going on. Opening a new terminal fixes this.

Is this actually a bug? If it is, does it matter at all? I'm guessing that the ability to watch some random characters scroll on the terminal isn't exactly the most important feature of Ubuntu...

I've attached a picture for clarification. I ran some basic terminal commands like "echo" and "free."

---

### Post by ibuclaw on 2008-11-21
heh...

My guess is this is **feature** (as proven by this [image]("http://www.cbttape.org/funny/bug3.jpg")) :D

type in the command:
```
reset
```

and tell us if this solves your issue.

Regards
Iain

---

### Post by ciscosurfer on 2008-11-21
It's not a bug.  See [http://en.wikipedia.org/wiki/Urandom](http://en.wikipedia.org/wiki/Urandom)

---

### Post by ItsJweed on 2008-11-21
> **ciscosurfer said:**
> It's not a bug.  See [http://en.wikipedia.org/wiki/Urandom](http://en.wikipedia.org/wiki/Urandom)

I think I might have missed something in the article, or I didn't describe the problem well enough. I understand that /dev/urandom is supposed to be an unblocked source of "random" bits. Therefore typing

```
cat /dev/urandom
```

puts a whole bunch of garbage on the screen. I expected it to do so. What I've noticed is that even after I stop the execution of this command, every character displayed in the terminal shows up as a different character. For example, typing

```
echo this this this
```

displays as 

```
$ &#9500;&#9252;&#9227;&#9149; &#9500;&#9252;&#9227;&#9149; &#9500;&#9252;&#9227;&#9149; &#9500;&#9252;&#9227;&#9149;
```

It's as if every character is randomly remapped to another character. This doesn't go away until you type "reset."

> **tinivole said:**
> 

type in the command:
```
reset
```

and tell us if this solves your issue.

Regards
Iain

Yes, reset fixes this.

Is this actually a bug then, or should I have expected this to happen? For example, typing 

```
cat /dev/zero
```

does not cause this error, nor does

```
cat /dev/random
```

> **tinivole said:**
> heh...

My guess is this is **feature** (as proven by this [image]("http://www.cbttape.org/funny/bug3.jpg")) :D


That gave me a good laugh.

---

### Post by ibuclaw on 2008-11-21
If you cat garbled text into a terminal, I guess one would expect this sort of behaviour to follow ;)

try:
```
cd /bin
cat *

```
And you will get the exact same result.

Regards
Iain

---

### Post by ItsJweed on 2008-11-21
> **tinivole said:**
> If you cat garbled text into a terminal, I guess one would expect this sort of behaviour to follow ;)

try:
```
cd /bin
cat *

```
And you will get the exact same result.

Regards
Iain

Fair enough. Thanks.

Jon

---

### Post by ItsJweed on 2008-11-21
> **tinivole said:**
> If you cat garbled text into a terminal, I guess one would expect this sort of behaviour to follow ;)

Actually, is it bad of me to ask why this happens? I'm really curious how printing raw/binary data could cause this to occur.

---

### Post by ibuclaw on 2008-11-21
I can't quite explain it myself, (had a small look round and haven't found a reason either), but it is an accepted feature in almost all things UNIX.

My best supplement.

If you are going to cat a file, check what it is first:
```
file **name_of_file**
```

If it turns out to be a binary/character special. Use another command to read from it.

There are a few to choose from:

```
## Prints all matched strings.

**strings** /dev/urandom

Outputs:
^i	&
xdo}
cV/	n
6pU@
R\$pY}
Azq2a
&!.V
Rg2*
t]	6
{i_/

```
```

## Prints Octal values

**od** /dev/urandom

Outputs:
0114400 162502 072473 132735 003757 047346 016532 151015 121023
0114420 036772 107035 133127 035671 176550 070564 176346 163017
0114440 104220 162350 001372 045361 162554 173103 052332 007224
0114460 107263 131217 006047 021116 030563 076504 004703 041013
0114500 170245 006155 140227 147131 033466 067227 051617 051074
0114520 002652 075335 173251 067611 017446 042577 027167 036722

```

```

## Prints Hex values

**hexdump** /dev/urandom

Outputs:
00123e0 32c2 8325 8e30 18cf 1f48 dec1 acb2 b3a3
00123f0 9fad 2385 2ce4 f61f 671c 8a37 a1e9 4540
0012400 c95e cfc1 0045 1a9f cd45 af3a 37e8 904f
0012410 0bcd 184a 5e19 14e1 3abf 2728 6a68 95d1
0012420 05df d179 7b9e 0541 dc60 5844 46f5 25aa
0012430 0855 3a52 f936 6393 9c27 dcd2 d95e baa7

```
And all won't harm your term session either :D

Regards
Iain

---

### Post by silverglade00 on 2008-11-21
cat * was freakin COOL!!! My Terminal blew up and flew off the screen with random Asian looking characters and my computer started beeping.

---

### Post by ciscosurfer on 2008-11-21
> **ItsJweed said:**
> Actually, is it bad of me to ask why this happens? I'm really curious how printing raw/binary data could cause this to occur.The short answer is because these files are compiled; they're not raw data.

---

### Post by ju2wheels on 2008-11-21
Its partially a result of character set (UTF8, ASCII) interpretation of binary data. You are trying to take information which represents commands or binary data and represent is as displayable characters. Not all combinations of data yield a displayable character, but rather actions. Evaluate a simple ASCII table and you will notice this. There are displayable characters and others which represent new line, console beep, etc.

---

