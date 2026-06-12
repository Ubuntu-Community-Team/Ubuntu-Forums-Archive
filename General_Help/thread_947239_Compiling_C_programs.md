---
title: "Compiling C programs"
date: 2008-10-14
forum: General Help
---

### Post by myquidproquo on 2008-10-14
Hi!

I'm having a problem compiling programs in c.
I made a simple HelloWorld program and when I try to compile it with 

gcc -c -Wall -ansi -pedantic hello.c -o hello

I don't get any error or warning but the "hello" file doesn't look like it's executable.
If I compile using gcc -v hello.c I can get it to work. Am I missing something?

Thank you.

---

### Post by justleen on 2008-10-14
that looks ok to me... (im not much of a C programmer, so what ever thats worth :) )

I use the following to compile c++
```

#/bin/sh
echo compiling C++ using -ansi -pedantic-errors -Wall
g++ -ansi -pedantic-errors -Wall $1 $2 $3

```
which is pretty much the same..

What happens if you dont specify a out file?

---

### Post by iaculallad on 2008-10-14
Compile the code first:

```
cc -c your_program_name.c
```

Create the executable file from the object file:

```
cc -o your_program_name your_program_name.c
```

and lastly, execute it:

```
./your_program_name
```

Just be sure that you're inside your working directory before executing the commands.

---

### Post by ad_267 on 2008-10-14
You're probably missing the "./" in front to execute the file. This says to look in the current directory.

---

### Post by myquidproquo on 2008-10-14
Doing it in steps work. 
But the other way still doesn't work.

When I do ls I find that the file is created but it doesn't show in green. If I try to run it I get a Permission denied.

---

### Post by iaculallad on 2008-10-14
> **myquidproquo said:**
> Doing it in steps work. 
But the other way still doesn't work.

When I do ls I find that the file is created but it doesn't show in green. If I try to run it I get a Permission denied.

What's the other way that didn't work? For the permission denied thing, try to insert your sudo with the execute command.

```
sudo ./program_name
```

You're working outside of your home folder?

---

### Post by myquidproquo on 2008-10-14
So in resume:

I can make it run using gcc -o hello hello.c

But I thought I needed -c somewhere...I guess I was wrong -c compiles without linking so the output file wasn't an exe, right?

Anyway, thank you all :)

---

### Post by ad_267 on 2008-10-14
You can use "chmod +x filename" to make a file executable.

Oops didn't read the previous post. Yes that's right. "-c" only does the compiling and produces an object file.

---

