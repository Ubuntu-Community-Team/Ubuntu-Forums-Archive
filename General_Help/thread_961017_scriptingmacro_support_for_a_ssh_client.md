---
title: "scripting/macro support for a ssh client"
date: 2008-10-27
forum: General Help
---

### Post by bioboi69 on 2008-10-27
Currently I use SecureCRT's scripting and macro support a lot in windows. I also modify my keyboard mapping in order to execute these scripts and macros. 

Is there any way I can have client side scripting / macros that are mapped to keys using a linux ssh client / terminal emulator combination?

Thanks

---

### Post by sdennie on 2008-10-28
I'm not completely sure what you are trying to accomplish but a fairly standard scripting mechanism for things like this is "expect".  To install it:

```

sudo apt-get install expect

```

Then, check the man page to see if it might suit your needs:

```

man expect

```

You can find lots of useful examples via google on how to use it for various things.

---

