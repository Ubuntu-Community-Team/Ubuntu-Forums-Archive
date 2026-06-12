---
title: "[SOLVED] C++ in ubuntu 7.10 gutsy"
date: 2008-09-07
forum: General Help
---

### Post by Diablo713 on 2008-09-07
Hello everyone,i used to write c++ (still a begginer) in windows,but now since i moved to ubuntu i wasn't able to start writing since i dont know how to install editors and compilers anyone knows how please help :).

---

### Post by omi291 on 2008-09-07
First, install the build-essential package through the command line(unless you already have it):

```
sudo apt-get install build-essential
```

Then, to compile all your code, navigate to the directory your source file is in, then type in this into the command line:

```
g++ <your_file_name>.cpp -o <executableName>
```

which will make an executable file with whatever name you specify as executableName. Then, to run the program, just type in:

```
./<executableName>
```

Here's another thread if you need it as well:

[http://ubuntuforums.org/showthread.php?t=113849](http://ubuntuforums.org/showthread.php?t=113849)

Hope everything works out :).

---

### Post by schauerlich on 2008-09-07
Editors are really up to personal choice. Gedit and Kate are both good graphical editors, and vi is a very powerful, although initially difficult to use command line editor. Gedit and vi are most likely already installed, and to install kate, go to Applications>Add/Remove and search for kate. For a compiler, open a terminal and run this command:

```

sudo apt-get install build-essential

```

There is also a Programming Talk subforum here that might be useful for questions about programming under Ubuntu. This FAQ is a good place to start: [http://ubuntuforums.org/showthread.php?t=796493](http://ubuntuforums.org/showthread.php?t=796493)

---

### Post by Diablo713 on 2008-09-08
Thanks that was really helpful!

---

