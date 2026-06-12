---
title: "How to download &amp; install an application?"
date: 2008-07-18
forum: General Help
---

### Post by Rebelli0us on 2008-07-18
I want to install Xnview. I found the files here:

[http://pagesperso-orange.fr/pierre.g/xnview/endownload.html](http://pagesperso-orange.fr/pierre.g/xnview/endownload.html)


Which file do I download?

After downloading, Ubuntu doesn't know what to do with the file!

I'm reading something about "enabling execute" attribute of the file... but really why is this so hard?

---

### Post by haegl on 2008-07-18
Download the rpm version and follow the instructions :
[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/]("http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/")

---

### Post by unoodles on 2008-07-18
first i would install the application alien.
(type: sudo apt-get install alien)
then download the .rpm file and open an terminal, type alien then drag and drop the file onto the terminal and hit enter, this will create a file with a .deb extension, which you can simply double click and install.
The reason it seems so hard is that the program is not under a free (as in speech) license. I would strongly recommend finding an open-source replacement in your add/remove programs.

---

### Post by pauper on 2008-07-18
This link should clear things up:

[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

Read about file permissions:

```
man chmod
```

---

### Post by Rebelli0us on 2008-07-18
Thank you. I'm just a clueless newbie, I don't see an .RPM file available on the download page. Also should I be looking for x64 version since I'm running AMD64 Linux? They only seem to list x86. I do understand the importance of open source (that's why I'm trying to get away from Windows) but Xnview is the best darn photo viewer out there, it's as good as ACDSee and it's free... it even loads Canon RAW format of my CHDK Canon A640 :)

---

