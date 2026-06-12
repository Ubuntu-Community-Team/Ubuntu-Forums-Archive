---
title: "Need wget alternative for website archiving"
date: 2008-10-17
forum: General Help
---

### Post by Christof999 on 2008-10-17
Hello, 

I download alot of webpages, that often contain pictures, archives and pdfs. I usually use wget to make a local mirror of the site and grab all the files off the site. Unfortunately sometimes wget doesnt work. For example, I tried downloading a website today (it had all kinds of zip and jpg files I wanted) and for some reason wget wouldnt download anything but the index page, even when the recursive option is used. 

I need some suggestions on alternative programs that might be able to work instead of wget.

Thanks 
Christopher

---

### Post by firefly2442 on 2008-10-17
I think some websites block wget using the user agent identification.  I think there is an option to change this in one of the commandline parameters, you might try that and see if it works.

---

### Post by iponeverything on 2008-10-17
Look at the index file that it downloaded.

As for as know, wget does not do CSS or javascript -- that might be your problem.. I don't know any cli wget type app that does, but if they exist you can find them with google.

---

### Post by p_quarles on 2008-10-17
> **firefly2442 said:**
> I think some websites block wget using the user agent identification.  I think there is an option to change this in one of the commandline parameters, you might try that and see if it works.
The -U argument in wget allows you to send a customized user agent string with the request. In other words, it's easy to tell the server that you're actually running Firefox. 

User agent switching is a common practice, and is often necessitated by poor html design -- but if wget is blocked, it is likely because the webmaster is concerned with bandwidth at some level. Please use wget responsibly and add --wait and and --limit-rate arguments to your scripts.

---

### Post by vanadium on 2008-10-17
You might want to try httrack, which is a specialized tool for archiving websites. It may be successfull in the cases where wget fails.

---

