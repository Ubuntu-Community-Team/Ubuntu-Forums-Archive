---
title: "Directory Loop?"
date: 2008-07-31
forum: General Help
---

### Post by HydroModeler on 2008-07-31
Ok here is the situation.  I am running Ubuntu 8.04 and somehow ended up with a directory in my Trash that I can't delete because it also contains it's self.  The file path looks like this:

trash:///_username/Desktop/username/Desktop/username...keeps going

Any help will be greatly appreciated.

---

### Post by ibuclaw on 2008-07-31
what does this do?
```
find $HOME/.local/share/Trash/files/ -type d -print
```
Regards
Iain

---

### Post by collinp on 2008-07-31
Run:
```
rm -rf  ~/.local/share/Trash/files
```

that should delete the trash directory itself. When it is needed it will recreate the directory.

---

### Post by HydroModeler on 2008-07-31
tinivole - I ran your command and it filled my terminal with username/Desktop/username/Desktop... for quite awhile and then came back to the prompt.  so i guess eventually the path ends.  no clue how it got there in the first place.

Hellow - I ran your command and it seems to have worked with out any unintended effects.  Thanks,  Any idea why empty trash didn't work but your method did?  Seems that empty trash should essentially perform that command.

---

### Post by collinp on 2008-07-31
> **HydroModeler said:**
> tinivole - I ran your command and it filled my terminal with username/Desktop/username/Desktop... for quite awhile and then came back to the prompt.  so i guess eventually the path ends.  no clue how it got there in the first place.

Hellow - I ran your command and it seems to have worked with out any unintended effects.  Thanks,  Any idea why empty trash didn't work but your method did?  Seems that empty trash should essentially perform that command.

my command "rm -rf ~/.local/share/Trash/files" forces deleting of the files directory that the trash is in. I dont know why it would not delete, i guess it just kept going around in a loop.

---

### Post by ibuclaw on 2008-07-31
> **HydroModeler said:**
> tinivole - I ran your command and it filled my terminal with username/Desktop/username/Desktop... for quite awhile and then came back to the prompt.  so i guess eventually the path ends.  no clue how it got there in the first place.


That is good, I was going to suggest what Hellow mentioned, but I just wanted to make sure that there was an end. :)

It appears that even linux has a limit as to how long the filesystem (after a small test I make it 4096 characters, which would make alot of sense, as it is divisible by 1024) directory length can be, and it seems that you somehow went above that limit :)

Regards
Iain

---

### Post by HydroModeler on 2008-08-02
> **tinivole said:**
> That is good, I was going to suggest what Hellow mentioned, but I just wanted to make sure that there was an end. :)

It appears that even linux has a limit as to how long the filesystem (after a small test I make it 4096 characters, which would make alot of sense, as it is divisible by 1024) directory length can be, and it seems that you somehow went above that limit :)

Regards
Iain

Iain - I figured you were headed that way, but just taking a stepped approach.  After running your command and seeing that there was in fact and end, i figured it was safe to run a recursive delete as suggested by Hellow

Thanks

---

### Post by chocoboman on 2012-03-31
Necroposting here, because I've got the same problem but rm -rf did not solve it.

It gives me a warning about "Circular directory structure" and does not delete the loop folder.

Any ideas?  :(

---

### Post by howefield on 2012-03-31
Old thread closed.

Please start a new thread.

---

