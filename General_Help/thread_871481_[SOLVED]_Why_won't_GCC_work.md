---
title: "[SOLVED] Why won't GCC work?"
date: 2008-07-27
forum: General Help
---

### Post by Neureo on 2008-07-27
I get the feeling the solution to this problem is fairly obvious, but I simply can't figure the darn thing out. I've looked at several guides for this, both on and offline, and they all say the same thing, but it doesn't work for me. 

I have a file called hello_world.c: 
```
#include <stdio.h>

int main() {
	printf("Hello, world!\n"); 
	return(0); 
}
```
I go to the terminal and type this: 
```
$ cd Sources
$ gcc hello_world.c
```
Nothing happens. I tried **$ ls** and saw that a new executable called a.out had been created. I tried both **$ a.out** and **$ hello_world**, but got **bash: hello_world: command not found**. 

What on Earth am I doing wrong? Thanks for your time!

---

### Post by ad_267 on 2008-07-27
You probably want to use "gcc -o hello_world hello_world.c"
-o is for output file.

Then ./hello_world or ./a.out to run it.

You need the "./" part before the name as it tells bash to look in the current directory.

---

### Post by era86 on 2008-07-27
Run ./a.out

must have the ./

---

### Post by Neureo on 2008-07-27
I see what you mean! I'm surprised none of the tutorials I read mentioned that. :/ Thanks!

---

