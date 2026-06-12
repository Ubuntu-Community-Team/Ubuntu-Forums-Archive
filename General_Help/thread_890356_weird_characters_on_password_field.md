---
title: "weird characters on password field?"
date: 2008-08-15
forum: General Help
---

### Post by aussiebuddha on 2008-08-15
Hi, I just installed a minimal ubuntu with the alternate cd cli installation and then installing gnome-core human-theme xorg.

Problem is. every time i type a password, i get some weird characters in the password field..

any ideas what this is?

---

### Post by forger on 2008-08-15
weird characters such as? could you take a screenshot?
are you sure you're using english to type it - i mean are you sure it's not in another language?

perhaps you need to install gksu or gksudo:
```
sudo apt-get install --reinstall gksu
```

---

### Post by forger on 2008-08-15
I'd suggest to also install [ubuntu-standard]("http://packages.ubuntu.com/hardy/ubuntu-standard"):
```
sudo apt-get install ubuntu-standard
```

---

### Post by aussiebuddha on 2008-08-15
see attached pic

---

### Post by aussiebuddha on 2008-08-15
> **forger said:**
> I'd suggest to also install [ubuntu-standard]("http://packages.ubuntu.com/hardy/ubuntu-standard"):
```
sudo apt-get install ubuntu-standard
```

i believe ubuntu-standard is what the alternate cd install when you select command line interface (what i did, so i have it installed already)

---

### Post by cariboo on 2008-08-15
From the looks of it may have your locales set wrong. To fix this error type:

```
sudo dpkg-reconfiugre tzdata
```

Jim

---

### Post by aussiebuddha on 2008-08-15
> **cariboo907 said:**
> From the looks of it may have your locales set wrong. To fix this error type:

```
sudo dpkg-reconfiugre tzdata
```

Jim

No, it didn't help :-(
That was my idea as well but i didnt know the command to fix it.

This is the second time I install it, and i get the same every time
weird!

this doesnt happen with the ubuntu full install.

maybe a package i'm missing?

---

### Post by donnykurnia on 2009-04-23
I recently upgraded from Intrepid to Jaunty, and I got the Yen character in password field, specially in firefox.

I suspect it is the gnome related problems, because the kde-based application like keepassx still have normal * character in password field.

This is the screenshot of password field in firefox:
[[img]http://img10.imageshack.us/img10/4863/screenshot08j.th.png[/img]](http://img10.imageshack.us/img10/4863/screenshot08j.png)

---

### Post by Leno. on 2009-04-23
Same thing happened to me. Anyone who knows where you can fix this?

---

### Post by chrishutt on 2009-04-25
Same problem but I also get an accented E wherever text is cut off to fit like in this screenshot of my gnome panel.

---

### Post by donnykurnia on 2009-04-29
I got the accent E from about a year.

---

### Post by natsmith9 on 2009-05-05
I'm experiencing the same issue.  I upgraded from 8.04 to 8.10 to 9.04 and now I'm getting these little weird characters. (i.e. Yen symbols in the password field, ellipsis replaced with a capital E with an accent in titles, and now i think quotation marks are replaced with a capital O with an accent over it as well in the titles)  I remember them popping up on occasion in 8.04, but after a restart it would be fine.  It doesn't affect performance or anything, but it's just so freaking annoying!  I've tried to do the things that were suggested earlier to no avail.

Any thoughts?

---

