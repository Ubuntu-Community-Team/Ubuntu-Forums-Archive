---
title: "[SOLVED] Trouble installing Lexmark driver"
date: 2008-08-08
forum: General Help
---

### Post by fullmetalgerbil on 2008-08-08
I have a Lexmark Z605 printer I'm trying to get working under Ubuntu. I visited this forum post-[http://ubuntuforums.org/showthread.php?t=49714]("http://ubuntuforums.org/showthread.php?t=49714") about installing the Lexmark Z600 driver which apparently works with the Z605 printer.
Unfortunately, when I tried to enter the terminal commands to unpack and install the tarred driver I kept getting error mesages telling me no such file or directory exists.
For example:
david@david-desktop:~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
david@david-desktop:~$ 
And:
david@david-desktop:~$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
tail: cannot open `z600cups-1.0-1.gz.sh' for reading: No such file or directory
The file is there, right on my desktop. I even tried putting it in its own folder and then unpacking it, but this is what I got:
david@david-desktop:~$ mkdir lexmark
mkdir: cannot create directory `lexmark': File exists
david@david-desktop:~$ 
So I'm flummoxed, to say the least.
Any help would be greatly appreciated.

---

### Post by x1a4 on 2008-08-08
Hi,
You must specify the location of the file, or navigate to the directory it's in
```
david@david-desktop:~$ tar -xvzf ~/Desktop/CJLZ600LE-CUPS-1.0-1.TAR.gz
```
or
```

david@david-desktop:~$ cd ~/Desktop/
david@david-desktop:~/Desktop$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz

```

---

### Post by Vivaldi Gloria on 2008-08-08
Or right click on it and choose exract.

---

### Post by fullmetalgerbil on 2008-08-08
Ok, thanks. Things seem to be moving along more smoothly now. I guess I just slipped up and assumed I was already in the desktop directory. Doh.

---

### Post by fullmetalgerbil on 2008-08-08
Actually, everything was going smoothly for the first command. After that, even when in the desktop directory, or when adding a path to that directory and file, nothing worked.
And as far as right clicking to extract via the archive manager, I tried it and yeah it extracted the tar.gz file-but I still couldn't get it to install.
Basically, I'm done. I'll just have to find a way to go buy an HPLIP supported printer so the thing has a chance of running under Ubuntu.

---

### Post by Temposs on 2008-08-11
hi. If you'd like, try my debian package for installing the z600 drivers:

[http://temposs.googlepages.com/liblexz600core0.deb](http://temposs.googlepages.com/liblexz600core0.deb)

Just set your printer to the Lexmark z600 once you install the driver.

Hopefully this can work for you :-)

---

### Post by fullmetalgerbil on 2008-08-11
Thanks, but it didn't work at all.

---

### Post by Temposs on 2008-08-12
That's odd. I've installed it for a Lexmark z611 and it worked fine, and someone else on the forums had success with it as well.

---

### Post by fullmetalgerbil on 2008-08-14
I guess that is odd. I heard that the z600 driver works with many models, including the z605. But alas, it did not work. Thanks anyways though.

---

