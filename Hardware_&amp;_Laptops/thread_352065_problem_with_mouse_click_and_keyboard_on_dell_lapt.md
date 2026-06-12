---
title: "problem with mouse click and keyboard on dell laptop"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by calcium79 on 2007-02-02
Hi, I'm using a Dell Inspiron 6400 w/ Core 2 Duo and an Intel 945GM "media accelerator", and basically the issue is that at various points the mouse click will stop responding in a session. I use GNOME.
I can fix the problem by pressing Alt+Escape and going to a new window. Occasionally it may stuff up in the midst of moving a window and the hand icon will just remain. I can move the mouse cursor around fine, the keyboard responds and the OS keeps working, but does anyone know what's causing the issue and how it could be fixed?

On a side note, sometimes the mouse reacts as though I clicked it twice, a nuisance when I click on Applications / Places / System and the menu comes up and closes instantly. The keyboard sometimes decides that when I press a key I've actually pressed it several times (for exaaaaaaaample) I haven't installed Intel graphics card drivers yet, but I don't really think that's related to the problem.

---

### Post by schruthensis on 2007-02-18
Having the same exact problem on a self built Tyan S2507T desktop machine.  

this is with ubuntu edgy 6.10 ...  same problem on a debian etch install on the same machine

---

### Post by schruthensis on 2007-02-22
worked around the problem by down-grading to Xubuntu 6.0

---

### Post by oddball on 2007-03-05
Noticed there has been a reply to this topic for a while...

I have a Dell XPS M1710 Laptop, and last night for a short while I was running the i686 version of Edgy, without any problems.  Then, I suddenly realised that I can now run the AMD64 version.

Since installing the AMD64 version I too have the exact same problems (Mouse stops clicking, keyboard repeat rate is a bit speedy when it feels like it).

I'm just about at my wits end, there doesn't seem to be any solution anywhere so any help is much appreciated.

Could it be a bug?
If so, where do I submit it?

Regards,
Oddball

---

### Post by snits on 2007-03-31
If you are having these problems on a system with Core 2 Duo try adding the "notsc" kernel parameter to the kernel boot line. 

Apparently this has been dealt with in more recent kernels.

---

