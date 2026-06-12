---
title: "Cannot write to floppy drive"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by tkpmep on 2005-09-21
I  installed Ubuntu Linux 5.04on a PC, used Open Office to create a Word document and then tried to copy the document to a floppy disk (I ensured that the floppy was writeable both by checking the position of the tab and by writing a file to it on my Windows PC). Unfortunately I get the following error message:

Error when copying to /media/ floppy0
You do not have permission to access this folder.

I then right clicked on the floppy icon and tried to change the  permissions from the permissions tab - it wouldn't let  me: the error message says that I cannot change the permissions for a read only floppy!

Following a suggestion, I then opened a root window and typed chmod 666 /media/floppy0. No luck. 

This is really my first experience with Linux: is there an easy fix for my problem?

Thomas Philips

---

### Post by mlomker on 2005-09-21
Open a terminal and type the following  

```

sudo mkdir /mnt/floppy0
sudo nano /etc/fstab

```

Type or paste the following line into the bottom of the file.

```

/dev/floppy0       /mnt/floppy0       vfat     defaults,users,noauto,umask=000  0  2

```

You can press Ctrl-X to exit, Y to save, and then Enter to accept the file name.

I'm guessing a little bit here because I don't have a floppy drive on my laptop.  The next time you restart it should work.  

If it doesn't let me know and I'll have you post the output of a couple diagnostic commands that'll ensure that I get it right.

---

### Post by tkpmep on 2005-09-22
Thank you very much - it worked - and I now have a follow up question, and help with it would be greatly appreciated:

Once again, I tried to change the permissions on the floppy drive by right clicking on it, selecting Permissions and checking Write. It still would not allow me to do so, but no nasty error message ensued. Why is not possible to change the permissions in this way?

On a more philosophical note, writing to a floppy is a very basic operation. Surely I should not have to ask for help with this (after reading your solution, I can confidently say that I would not have arrived at this solution on my own). Is this a flaw with Linux, or the result of a bad choice of  installation options (I think I chose the defaults)?

Sincerely

Thomas Philips

---

### Post by mlomker on 2005-09-22
>  Is this a flaw with Linux, or the result of a bad choice of  installation options (I think I chose the defaults)?


It isn't you.  I've been trying linux annually for the last five years or so and this is the first time that I've stuck with it for more than a week!  I'm a Windows networking administrator for a living and I had a hard time getting a usable desktop in the past.  Linux has made great progress.

The fundamental problem with linux today is that it is free.  You have a lot of programmers working on things that interest them and then they throw it all together and, unsurprisingly, it doesn't always fit together.  

Up until recently only for-profit companies (like Microsoft) had the money to hire project managers and usability experts.  It's easier to find obsessive programmers to volunteer their time than business people. Today there are corporate sponsers and non-profits that are getting substantial funding now that linux has gained some momentum.

---

