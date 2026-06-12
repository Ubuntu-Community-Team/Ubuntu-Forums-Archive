---
title: "Cant get 1280x800 resolution to work"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by tripleZero on 2006-11-02
I am running Ubuntu 6.06 on vmware, and I cant get the resolution to 1280x800.  I already installed vmware tools.  I have a dell inspiron 700m with a intel 82852/82855 GM/GME graphics controller.  Any body got any ideas?

Thanx in advance.

---

### Post by tripleZero on 2007-02-22
this one took me while to figure out, but when i did man was it worth it.  i had to reconfigure the xserver, i forgot the exact command but google it and u should find something.  when you do that a screen will appear and ask you to choose a bunch of options.  for me everything was already the way it needed to be, the only thing i had to change was when the options for the screen resolution appeared.  i picked 1280x800 because that is what i needed, but there was bunch of other options.  after that just restart the xserver (ctrl+alt+backspace) and like magic it works.

---

