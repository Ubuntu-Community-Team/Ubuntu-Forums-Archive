---
title: "Help needed. Can't get my Canon Pixma MP600 working in my amd64 laptop with Hardy"
date: 2008-08-29
forum: Hardware
---

### Post by a3qp on 2008-08-29
Hi, I'm new at ubuntu, and I really need a howto tutorial about getting Pixma mp600 working on ubuntu hardy amd64.

I have read: 
[http://mp610.blogspot.com/](http://mp610.blogspot.com/)
and
[http://ubuntuforums.org/showthread.php?t=456751](http://ubuntuforums.org/showthread.php?t=456751)

but I have not compiled without all the code steps. They assume some things that you should know, and unfortunately I don't. Anyone can help me step by step? 

I'm sure I'm not the only one in this situation.

Thanks,

---

### Post by cariboo on 2008-08-29
Which step are you having problems with?

Jim

---

### Post by silvanus2005 on 2008-08-29
[http://software.canon-europe.com/software/0027403.asp?model=](http://software.canon-europe.com/software/0027403.asp?model=)
Try that driver, perhaps it will work on your AMD64 version.

---

### Post by a3qp on 2008-08-29
Hi Cariboo, thanks for your reply.

let's follow [http://mp610.blogspot.com/](http://mp610.blogspot.com/) to make it easier.

First it says:
"As promised, here is a quick guide for compiling SANE CVS version, which always contains the latest release of SANE pixma backend. This is a better solution to get Sane CVS lib and compile it, than to use the Standalone driver, available from this blog.
The CVS version now supports most recent PIXMA models ....in addition to all older older pixma models"

ok, so as my model is MP600, it should be in "in addition to all older pxma models". So, let's go.

* Download latest SANE CVS package

I'll use the first method (since the other says: "as developers do" and I feel I will have more problems).

method 1: Download the SANE tar.gz nightly snapshot package

I go to: [http://alioth.debian.org/scm/?group_id=30186](http://alioth.debian.org/scm/?group_id=30186)


As those instructions: "cvs -d :pserver:anonymous@cvs.alioth.debian.org:/cvsroot/sane login" don't work (since I don't have cvs installed), I click:

[Download The Nightly CVS Tree Snapshot] 

and inmediatelly a popup window offer me to save the file sane-scm-latest.tar.gz. Then I go to the folder and open it with Archive manager, and I extract it in the same folder.

I got 6 subfolders inside the folder sane-scm-2008-08-29, and I guess it is ok so far.

Then it says:

"* Build SANE

Enter the directory sane-backends created after downloading SANE CVS."

Then it says:
"Check first that the development libusb library is present and installed.

on Ubuntu, it is called: libusb-dev.

Install the package, if not already installed."


First 3 questions.

How can I check if the libusb library is present and installed ?
Where do I have to see written libusb-dev?
How can I installed the package if not already installed?

Thanks.

---

### Post by a3qp on 2008-08-29
Thanks Silvanus2005, but those are the files that I've been having problems with. They are for the 32bit version, and as far as I understand, I have to do a tweak with them (use a live cd of 32 bit, something like that)... I'm hoping not to have to do that with this other method.
Let's see.

---

