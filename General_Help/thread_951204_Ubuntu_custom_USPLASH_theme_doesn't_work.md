---
title: "Ubuntu custom USPLASH theme doesn't work"
date: 2008-10-17
forum: General Help
---

### Post by Naatan on 2008-10-17
Hi, I followed the following steps to install the usplash theme on that page:

[http://www.gnome-look.org/content/show.php/show.php?content=79631&vote=good&tan=48919193](http://www.gnome-look.org/content/show.php/show.php?content=79631&vote=good&tan=48919193)

However now when I boot my screen looks like some sort of template, check the screenshot for details.

I am using Ubuntu 8.10 beta so it might be related to that, but I thought I'd check here first to see if anyone had this before..

---

### Post by Naatan on 2008-10-18
bump

---

### Post by Naatan on 2008-10-18
bump again

---

### Post by theozzlives on 2008-10-27
I don't get usplash in 8.10 RC except the default

---

### Post by morepowerr on 2008-10-28
I have been having same problem. And after playing with it most the day. All I can think of is something in uplash has changed. And the 8.04 .so will need to be made. 

 But with out looking at the source from both. I cant say what it is.
 We will just have to hope they get it looked at soon.

 From what I have read on gnome-look.com he/she knows the .so are not working in 8.10

from perfectska04: "I'll probably get around to uploading binaries compatible with Intrepid once it's out officially."

So all I can say for now is give it a week or so.

--powerr

---

### Post by Naatan on 2008-11-01
> **morepowerr said:**
> I have been having same problem. And after playing with it most the day. All I can think of is something in uplash has changed. And the 8.04 .so will need to be made. 

 But with out looking at the source from both. I cant say what it is.
 We will just have to hope they get it looked at soon.

 From what I have read on gnome-look.com he/she knows the .so are not working in 8.10

from perfectska04: "I'll probably get around to uploading binaries compatible with Intrepid once it's out officially."

So all I can say for now is give it a week or so.

--powerr

I've had the issue with multiple .so's though.. but that might just be cause Intrepid is still quite new and most developers probably haven't bothered about the compatibility.

Thanks for your reply morepowerr..

---

### Post by morepowerr on 2008-11-05
ya I fond a way around it but probity not the best way.

[http://ubuntuforums.org/showthread.php?t=967130](http://ubuntuforums.org/showthread.php?t=967130)

---

### Post by red_team316 on 2008-11-07
There is nothing wrong with usplash in 8.10 Intrepid. Anyone wanting to use a custom usplash will have to recompile it on an Intrepid box.

There were obviously changes to usplash from Hardy 8.04 to Intrepid 8.10. One of those changes was changing the THEME VERSION to 3. I'm not 100% sure if this is the reason why the old usplashes wont work, but I'm betting on it. A dapper(THEME VERSION 1) usplash doesn't work on Edgy(THEME VERSION 2). It makes sense to me that a hardy(THEME VERSION 2) usplash theme does not work on intrepid(THEME VERSION 3).

[https://launchpad.net/ubuntu/+source/usplash](https://launchpad.net/ubuntu/+source/usplash)

Somebody just needs to update the Usplash Customization page as to what we can do with the new API changes...

---

