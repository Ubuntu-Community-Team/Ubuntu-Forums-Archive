---
title: "Gcc"
date: 2008-07-17
forum: General Help
---

### Post by iampriteshdesai on 2008-07-17
I have just started programing and am currently studing C and C++. I have read that Ubuntu comes with Gcc. I tried but couldn't found it. So thanks to googling I installed GCC using the live cd and the command 
sudo apt-get install build-essential

in the terminal.
Then I typed man gcc in the terminal this brought gcc manual. Next what? How can I start writing? Can I find GCC program some where? Is coding on Ubuntu diff from coding on Windows?
Plz explain everything upto the point of getting the point of writting

---

### Post by mali2297 on 2008-07-17
> **iampriteshdesai said:**
> I have just started programing and am currently studing C and C++. I have read that Ubuntu comes with Gcc. I tried but couldn't found it. So thanks to googling I installed GCC using the live cd and the command 
sudo apt-get install build-essential

in the terminal.
Then I typed man gcc in the terminal this brought gcc manual. Next what? How can I start writing? Can I find GCC program some where? Is coding on Ubuntu diff from coding on Windows?
Plz explain everything upto the point of getting the point of writting

GCC is just a compiler. If you have written a source file, say foo.c, you can compile it from the terminal with the command
```

gcc foo.c -o foo

```

If you are looking for an IDE (Integrated Development Environment), then check out, for example, Anjuta or Code::Blocks.

Also, check out the [Programming talk]("http://ubuntuforums.org/forumdisplay.php?f=39") section, especially the sticky.

---

