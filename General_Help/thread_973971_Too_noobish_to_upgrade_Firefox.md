---
title: "Too noobish to upgrade Firefox"
date: 2008-11-07
forum: General Help
---

### Post by contrariwise on 2008-11-07
I've been trying to upgrade Firefox for...a day now.  Since I couldn't run Firefox due to an error telling me that I need GTK+2.10 or newer, I followed [these]("http://ubuntuforums.org/showthread.php?t=927626") instructions.  When I run ./configure, I get:

```
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.17.6    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

Requested 'glib-2.0 >= 2.17.6' but version of GLib is 2.10.3
Requested 'atk >= 1.13.0' but version of Atk is 1.11.4
Requested 'pango >= 1.20' but version of Pango is 1.12.3
Requested 'cairo >= 1.6' but version of cairo is 1.0.4

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I tried to find the relevant stuff in the synaptic package manager, but I don't see anything with quite those names, so I'm not sure what exactly I need.  I appreciate anyone who would like to enlighten me.

---

### Post by vikrant82 on 2008-11-07
It seems you are trying to compile firefox. This needs installing a lot of development libraries. You can try your luck by first installing dependencies :

```
sudo apt-get build-dep firefox
```

Well, it seems you already have some development libraries, but you are trying to compile a later version firefox which depends on newer development libraries. I don't see the need of it since there are so many places from where you can get the ubuntu binaries(read debs).

Are you trying to build firefox 3.1 beta from svn, if you are trying that then there are certian PPAs which will give you intrepid debs.

Or otherwise post which version you are trying to upgrade to.

---

### Post by contrariwise on 2008-11-07
Thank you for your reply.  I'm sorry, but I understood about 8% of what you said!  I'm just trying to upgrade to Firefox 3.0.3 and make it work, so I followed the instructions that I linked to.  The code you gave me doesn't appear to make a difference and I didn't understand the rest of it.  PPA's?  Intrepid debs?

---

### Post by kerry_s on 2008-11-07
put simply, firefox 3 is not made to run with your current software/libraries, it requires newer than what you have. you won't get it working unless you update everything firefox depends on, which could break other things.
you could try adding the ubuntu repo that has that version, but than it could break other things as well. all depends on how bad you want it.
if you have at least firefox 2.0.0.17 your okay, it's still supported security wise. i use 2.0.0.17 in debian etch.

---

### Post by contrariwise on 2008-11-07
But it says I only have four things that I need to update.  Can't I just update those four things somehow?

---

### Post by kerry_s on 2008-11-07
never mind

---

