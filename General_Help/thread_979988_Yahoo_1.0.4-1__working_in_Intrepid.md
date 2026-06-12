---
title: "Yahoo 1.0.4-1  working in Intrepid"
date: 2008-11-12
forum: General Help
---

### Post by rfm33428 on 2008-11-12
I got Yahoo Messenger working in Intrepid.  I unpacked the .deb file.  Ignoring the dependencies warning, I went to the location & ran the messenger & it worked beautifully.

However, there was a side effect with the package manager. It comes up with an error in the dependencies.  If there's a way to disable the package manager from detecting ymessenger, IDK.  That would be a plus.

Other than that, knock on wood,  I'm having no problems.

Out of all the articles I've search & read, nobody has even mentioned anything like this.  So I decided to give it a shot just to see what happens.

---

### Post by Jakey_TheSnake on 2008-11-12
Presumably if it's a .deb it was designed for linux?...or is it me :neutral:

---

### Post by rfm33428 on 2008-11-12
Yeah, but there were issues because it depended on other packages that were replaced with newer ones.  libglib2.2  and there was something else  0.9.6.   Idk why, but it wouldn't accept anything else.   Seems to like a dependancy flaw or something, not to accept newer versions of that package(s).  Well, that's just my opinion.  I'm sure there's a logical reason, that I don't know about.  :lolflag:

---

### Post by rfm33428 on 2008-11-13
I discovered something the hard way about having an error in the Package Manager, you can't install new packages and get updates.  So, as much as it is an inconvenience, fix the broken package (removing ymessenger) then install your other packages and/or get any updates.  Finally re-install ymessenger.

I know, it's more work than you want to do.  However, it's a nice work around to having ymessenger & being able to install other packages and updates.

---

