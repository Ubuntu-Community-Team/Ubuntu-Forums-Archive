---
title: "Quick Question (really! :P)"
date: 2008-09-27
forum: General Help
---

### Post by Xonara on 2008-09-27
I just compiled a simple 'Hello World!' program and I was looking for easier ways to launch it other than typing ./test in the terminal. I found a launcher worked if I set it to run in a terminal. However, I also tried give the program a .sh extension, which I didn't expect to work at all... But it did. Huh? I thought shell scripts are in plain text and executables are in binary... How is this possible? :confused:

---

### Post by Bakon Jarser on 2008-09-27
Lots of plain text files are executable.  In windows all those .bat files you see are plain text.  I'm just about to start learning python and from what I know so far all the .py are just plain text executable files.  Makes them a lot easier to edit.

---

### Post by Xonara on 2008-09-27
But changing the extension doesn't actually change the file type... If I'm understanding right, the executable is binary and shell scripts are ASCII codes so the console shouldn't be able to run it if it's trying to open it like a shell script... I know I'm not understanding something here, what am I getting confused over? :/

---

### Post by Aearenda on 2008-09-27
Linux doesn't rely on file extensions alone to determine filetypes, unlike Windows. It looks inside the file, and recognises a binary executable regardless of name. An executable shell file is recognised by the #!/bin/bash or similar in the first line. 

Are you really wanting just to avoid typing "./" when running your program? This is required because the loader search path does not include the current directory, which it does on Windows.

---

### Post by Xonara on 2008-09-27
What's confusing me is that, normally when I click the program nothing happens, because it's supposed to run in the terminal. Running it from the terminal works fine. But when I put a .sh extension on it and try to run it, a dialog pops up saying it's an *executable text file*, when it really isn't. What I'm trying to say is that Ubuntu tries to handle it like a shell script, and actually succeeds in running it... The only explanation I can think of is that the dialog pops up and tries to handle the file like  .sh, but when I click run in terminal the file is checked again and handled like a binary file... Meh.

---

### Post by RequinB4 on 2008-09-27
> **Xonara said:**
> What's confusing me is that, normally when I click the program nothing happens, because it's supposed to run in the terminal. Running it from the terminal works fine. But when I put a .sh extension on it and try to run it, a dialog pops up saying it's an *executable text file*, when it really isn't. What I'm trying to say is that Ubuntu tries to handle it like a shell script, and actually succeeds in running it... The only explanation I can think of is that the dialog pops up and tries to handle the file like  .sh, but when I click run in terminal the file is checked again and handled like a binary file... Meh.

A shell script *is* a "binary" (executable text file) file if it's runnable - thats why you have to chmod +x it.

As for renaming to .sh, that doesn't matter one bit in linux.  I could rename one of my shell scripts to EVILzylords.reallycoolfile.notreally.yay and it would run.

---

### Post by Aearenda on 2008-09-29
Actually I think what Xonara has noticed is valid - if the file has a .sh extension, Nautilus will try running the program in a shell, so it works, but if it does not have .sh, it fails to run as there is no shell environment present, which it needs. It is still started, but fails silently.

---

