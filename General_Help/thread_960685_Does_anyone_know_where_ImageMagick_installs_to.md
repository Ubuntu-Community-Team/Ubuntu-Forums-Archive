---
title: "Does anyone know where ImageMagick installs to?"
date: 2008-10-27
forum: General Help
---

### Post by khughitt on 2008-10-27
I'm trying to install some software from source, but it has been having trouble finding ImageMagick:

```
Error! ImageMagick version 5.5.7 or later is required but was not found
       Use --with-Magick=DIR to specify the ImageMagick directory tree
       Use --with-Magick=no  to not use it
       Check the README or use configure --help for other libraries needed
       (--with-xxxdir = obligatory, --with-xxx = optional (--with-xxx=no to disable))
```

Even though it *is* installed on my system:

```
Package: imagemagick
State: installed
Automatically installed: yes
Version: 7:6.3.7.9.dfsg1-2ubuntu3
```

Does anyone know where imagemagick is located? I couldn't find it anywhere.

Thanks!
Keith

---

### Post by Sam on 2008-10-27
```
dpkg -L imagemagick
```
or
```
locate imagemagick
```

---

### Post by khughitt on 2008-10-27
Thanks Sam!

That's very useful to know. I've used locate before, but remember reading somewhere that it uses a cache which may not always be up-to-date, and I always just used "find" instead.

The dpkg command was even more useful and I've never seen that before. Unfortunately the tarball I'm trying to install still is unable to find the files it's looking for (perhaps something that an older version of ImageMagick used to have). Oh well.

Take care,

---

### Post by Sam on 2008-10-27
> **pwnedd said:**
> I've used locate before, but remember reading somewhere that it uses a cache which may not always be up-to-date

In this case, use```
sudo updatedb
```;)

---

### Post by Senplanet on 2010-12-13
I have the same problem. My ImageMagick is version 7:6.6.2.6-1ubuntu1.1 but when I try to configure GDL the same error appear. 
Did you find any solution?

---

### Post by tredegar on 2010-12-13
> but when I try to configure GDL the same error appear. 
I don't know what "GDL" is, but...

I have just read through those (old) posts.
The OP was referring to "installing from source".

If that is what you are also trying to do, then I think the error is not about the *package* imagemagick but it is looking for the *source files* for imagemagick.

In which case you need to install the imagemagic dev(elopment) package(s). Looks like it might be called **libmagiccore-dev** so install that, and try again. You might also need **libmagic++-dev**

---

