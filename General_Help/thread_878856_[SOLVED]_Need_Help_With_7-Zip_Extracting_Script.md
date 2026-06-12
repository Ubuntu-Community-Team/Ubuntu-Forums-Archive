---
title: "[SOLVED] Need Help With 7-Zip Extracting Script"
date: 2008-08-03
forum: General Help
---

### Post by HotDogBunToo on 2008-08-03
Well, I already have a feel for 7-Zip and how to get stuff extracted, except I'm trying to simplify things with a script and do things with a script instead of always writing it out in command line.  

I want to just be able to right click on a archive file (whether it be zip, rar, 7z or whatever) open it with script, and have the script execute it & extract the file within the current subfolder that the archive file is located in... for example

```

7z x "/media/nicely/coolfiles.rar" -o"/media/nicely/coolfiles"

```

is needed so everything extracts in the /coolfiles/ folder, otherwise if I omit the -o switch and just type

```

7z x "/media/nicely/coolfiles.rar"

```

then everything will just go to the $HOME directory... not what I want :\ 

Thus I don't always feel like typing things out in command line and just want the script to do the job after just opening file in directory... yet the only thing I can come up with is 

```

#!/bin/sh
7z x "$*"
```

Which of course only extracts it to the home folder.  Not sure how to have this dynamically extract to a specific folder where the archive file exists via script (for the -o switch) so any help on this would be appreciated.

---

### Post by ogredeschnique on 2008-08-03
[Edit]
Deleted by user.

---

### Post by pietjanjaap on 2008-08-03
[http://k7z.sourceforge.net/](http://k7z.sourceforge.net/)
Install  the gui for 7z.

---

### Post by HotDogBunToo on 2008-08-03
Thanks pietjanjaap,

It's easier to work with a GUI interface, but doesn't do anything for me when I either drag a rar file to it or try to open a file with it... so unless there's another GUI that'll be more streamline, i'll still need to come up with a script :/

---

### Post by zvacet on 2008-08-03
Doesn´t p7zip work like you want to?Right click on archive and select **extract here**.

---

### Post by kostkon on 2008-08-03
> **zvacet said:**
> Doesn´t p7zip work like you want to?Right click on archive and select **extract here**.
I want to ask the same thing.

Or double click on it and open it with the archive manager.

---

### Post by HotDogBunToo on 2008-08-04
> **kostkon said:**
> I want to ask the same thing.

Or double click on it and open it with the archive manager.

Thing is, the archive manager will work with many archive files, however I have a ton of .RAR archives that won't work thus me specifically using 7zip via the 7z command.

---

### Post by angry_johnnie on 2008-08-04
I think installing **rar** and **unrar** will allow you to extract (and compress) .rar files by right clicking, or via archive-manager.

---

### Post by HotDogBunToo on 2008-08-04
> **angry_johnnie said:**
> I think installing **rar** and **unrar** will allow you to extract (and compress) .rar files by right clicking, or via archive-manager.

Wow,

Yea that sure did the trick, thanks!!!

Guess for the mean while I'll figure out this scripting stuff as a means of killing the curiosity and eventually post that if I ever get that figured out... but as far as getting the job done of handling these rar files this works perfectly.  Thanks for the help all!

---

