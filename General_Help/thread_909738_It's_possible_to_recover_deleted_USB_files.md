---
title: "It's possible to recover deleted USB files?"
date: 2008-09-03
forum: General Help
---

### Post by ruipedroca on 2008-09-03
Hi,

I've made a huge mistake: 

I've deleted (shift+delete)all the data of my 4gb usb pen without making a backup! Is it possible to recover it? 
It's FAT or FAT32 (I can't remember) filesystem!



If so, explain how, please!

---

### Post by Gannon8 on 2008-09-03
Yeah, use a program like photorec to recover it.
```
sudo apt-get install photorec
```(I don't remember, is it downloadable using apt?)

---

### Post by drs305 on 2008-09-03
There is also [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") which says it can undelete files on FAT file systems.

Here is an ubuntu link on data recovery in general:
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by Cope57 on 2008-09-03
Those are some good recommendations I hope it works for you.
I never have been able to recover anything from a deleted flash drive without plugging it into the OS that deleted it in the 1st place.
But if you did delete your flash drive while using Ubuntu. Go look in your trash can, everything should be there unless.... you emptied the trashcan. Sorry, but that is all I can say to help.

---

### Post by ruipedroca on 2008-09-04
Well, I've recovered all my files!

I've installed TestDisk and then ran Photorec in the konsole. 
It was very much simple and I just had to let the computer turned on all night to let Photorec run.

However, now I see that dispite I've recovered all the files, they haven't the original name, nor the folders!
They all have a strange name like f5478545.txt or f54784.html...

So I'd have to open all the files to know what's inside, what is useless in my case because my major concern were the Thunderbird portable email client and here the file names play an essential role. 

If anyone has an idea of how to turn around this situation, please let me know.


Regards

---

### Post by greco8523 on 2008-09-04
You may want to be careful how you handle the drive when you are recovering the data. Be careful not to save the files back on to the USB drive this will definitely ruin your chances. 

Some links that will help:
[www.datarecoveryadvice.org](www.datarecoveryadvice.org) 
[http://en.wikipedia.org/wiki/Data_recovery](http://en.wikipedia.org/wiki/Data_recovery)

---

### Post by ruipedroca on 2008-09-10
Hi,

I've managed to recover all my files doing this:

1 - I've installed the program "Undelete" which is completly free in a windows instalation.
(:oops: I've managed to install it with Wine, I didn't knew how to make it detect the USB pen or use the image of it I've created)

2 - I've ran the program and it recovered every file and folder and, most important, the file structure! \\:D/

I've noticed, after running Thunderbird portable, that some of my emails were in the wrong folder and some were with strange subjects, but this happened only to about 1 on 30 emails or so.


To finish, I've just made a backup! :guitar:

Hope this experience might help somebody!


Regards

---

