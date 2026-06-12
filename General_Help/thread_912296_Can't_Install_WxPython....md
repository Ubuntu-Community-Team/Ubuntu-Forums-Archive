---
title: "Can't Install WxPython..."
date: 2008-09-06
forum: General Help
---

### Post by yrrej on 2008-09-06
Hi,

I am just becoming acquainted with Ubuntu 8041...

I tried to install wxPython via synaptic but when I tried
the 2.8 package I got a corrupt tar file message from
libwxgtk-2.8 and the install failed...

I then tried to install the 2.6 package... it installs
but an import wx command gives a missing

ImportError: /usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core_.so: undefined symbol: _ZN5wxApp12ms_classInfoE, version WXU_2.6

So,

How can I get wxPython up and running?

Jerry

---

### Post by dannyboy1121 on 2008-09-06
Out of curiosity - did you try 2.8 more than once and get the same message? I would be surprised if the repository version was corrupted - I imagine that it's all md5sum verified.

---

### Post by yrrej on 2008-09-06
> **dannyboy1121 said:**
> Out of curiosity - did you try 2.8 more than once and get the same message? I would be surprised if the repository version was corrupted - I imagine that it's all md5sum verified.

Yes I tried several times...

Jerry

---

### Post by yrrej on 2008-09-06
Ok,

I removed all of the residue of the failed attempt and reloaded the
"bad file" first then the rest of the wx python thingees an the install
seems to be working....


Jerry

---

