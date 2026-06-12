---
title: "Automate using shell script"
date: 2008-07-23
forum: General Help
---

### Post by retrow on 2008-07-23
After writing a C code for a task, I want to automatically compile and execute the latest modified code. I have reached till listing the last modified file, but I don't know how to separate out the file name from the extension.

Suppose my latest code is fourier2d.c, I compile and run it with:
```
gcc -o fourier2D fourier2D.c && ./fourier2D
```

But instead of having to specify a filename (fourier2D in this case) each time, how do I use a shell script to do the task for me?
```
cd /home/user/programming
newfile=`ls -rt *.c | tail -1`
gcc -o $newfile $newfile.c && ./$newfile
```

Now this doesn't work, because it uses the *.c* extention everywhere. Which is why I am trying to separate out *.c* from rest of filename. Any suggestions how I can do it?

Thanks a lot.

---

### Post by sdennie on 2008-07-23
Try:

```

cd /home/user/programming
newfile='ls -rt *.c' | tail -1'
binary=`basename $newfile .c`
gcc -o $binary $newfile.c && ./$binary

```

Though, if you have the time, you may just want to learn how to write quick makefiles to accomplish this.

---

### Post by retrow on 2008-07-23
Thank you very much, vor!

*basename* command worked like a charm. The final code looks like this:

```
#!/bin/bash

cd /home/user/programming
newfile=`ls -rt *.c | tail -1`
binary=`basename $newfile .c`
gcc -o $binary $newfile && ./$binary
```

---

