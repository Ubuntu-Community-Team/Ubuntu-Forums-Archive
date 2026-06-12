---
title: "Updating GTK on Ubuntu 8.10"
date: 2008-10-31
forum: General Help
---

### Post by Aizawa on 2008-10-31
I'm installing Midori (The web browser). I could just install it from the repositories, but that's 0.0.21, and you can get 0.1.0 from the website, so I want that one. Because 0.0.21 crashes nearly every time I click a link, basically.

However, installing midori requires GTK+-2.6.0 or higher, and apparently only 2.0 is installed on my PC.

So, is there an easy way to update it? Is there an easy way to update all programs/libraries? 'Cause the option to just updating it (if that is an option) is apparently downloading a tarball and compiling it, and since I'm sorta fresh to Linux I'd rather not do that.

Sorry if there's already a thread about this.

---

### Post by Yellow Pasque on 2008-10-31
I think you're reading it wrong. Intrepid has libgtk2.0-0 version 2.**14**.x
14 > 6

EDIT: If that doesn't make sense, look at the version history of libgtk through releases of Ubuntu: [http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libgtk2.0-0](http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libgtk2.0-0)

---

### Post by Aizawa on 2008-10-31
Well. In that case I'd need help with something else, perhaps I misunderstood the error message. As said, I'm not very good with Linux.

When installing Midori I first extract it from the tarball, of course. I cd to the directory, type ./configure..

Checking for Python			:  033[92m/usr/bin/python033[0m
Checking for WAF			:  033[92m/home/walrus/midori-0.1.0/waf033[0m
calling waf configure with parameters
Checking for program gcc                 : ok /usr/bin/gcc 
Checking for compiler version            : ok 4.3.2 
Checking for program cpp                 : ok /usr/bin/cpp 
Checking for program ar                  : ok /usr/bin/ar 
Checking for program ranlib              : ok /usr/bin/ranlib 
Checking for compiler could create programs : ok  
Checking for compiler could create shared libs : ok  
Checking for compiler could create static libs : ok  
Checking for flags -O2                         : ok  
Checking for flags -g -DDEBUG                  : ok  
Checking for flags -g3 -O0 -DDEBUG             : ok  
Checking for flags -Wall                       : ok  
Checking for gcc                               : ok  
Checking for program rst2html.py               : not found 
Checking for program rst2html                  : not found 
Checking for generate user documentation       : not available 
Checking for program msgfmt                    : not found 
Checking for program intltool-merge            : not found 
Checking for header locale.h                   : ok  
Checking for localization support              : not available 
Checking for localization file updates         : no 
Checking for generate API documentation        : no 
Checking for package unique-1.0 >= 0.9         : not found 
Checking for single instance support           : not available 
Checking for package gio-2.0 >= 2.16.0         : not found 
Checking for GIO support                       : not available 
Checking for package sqlite3 >= 3.0            : not found 
Checking for header sqlite3.h                  : not found 
Checking for header sqlite.h                   : not found 
Checking for history database support          : not available 
Checking for package gtk+-2.0 >= 2.6.0         : not found 
pkg-config cannot find gtk+-2.0 >= 2.6.0 


So perhaps something if messed up with pkg-config, then..

---

### Post by Aizawa on 2008-10-31
I mean, there's a lot of other "missing" and such messages, but it doesn't stop the entire ./configure..process..thing.., so I didn't think it was important.

---

### Post by Yellow Pasque on 2008-10-31
You'll need the development library packages for midori's requirements. So,
```
sudo apt-get install libgtk2.0-0-dev libwebkit-dev libsqlite3-dev libunique-dev libglib2.0-dev libxml2-dev libgtksourceview2.0-dev xdg-utils build-essential
```

---

