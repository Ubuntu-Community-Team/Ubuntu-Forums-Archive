---
title: "[SOLVED] Photograph resizing software - recommendations?"
date: 2008-10-14
forum: General Help
---

### Post by Kevbert on 2008-10-14
I've a number of large-ish photos which are in jpg format and I'd like to use them on a mobile phone (jpg also).  Can anyone recommend a good Ubuntu application for this ?

---

### Post by hyper_ch on 2008-10-14
gimp?

---

### Post by patrickballeux on 2008-10-14
Hi,

There is an add-on on Nautilus to resize image from the contextual menu.

Install the package "nautilus-image-converter" and you will be able to do mass resizing without having to open any software.  Quite useful.


To install from a terminal: 

```
sudo apt-get install nautilus-image-converter
```

Good luck!

---

### Post by Kevbert on 2008-10-14
That works well on single pictures, thanks. Is there something I could do on a number of pictures in one go without having to load them one at a time ?

---

### Post by hyper_ch on 2008-10-14
imagemagick... it's a command-line program often used on webpages.

---

### Post by Kevbert on 2008-10-14
Thanks. Installed and up and running.

---

### Post by patrickballeux on 2008-10-14
> **Kevbert said:**
> That works well on single pictures, thanks. Is there something I could do on a number of pictures in one go without having to load them one at a time ?

It works also on multiple pictures, you simply have to select more than one in Nautilus...

---

### Post by sub2007 on 2008-10-14
gThumb. Works a treat. Even though I have Gimp I use GThumb for resizing/cropping/conversion because it's so light, fast and is very easy to use. I'm pretty sure it can also do batch operations for multiple images but don't hold me to that.

---

### Post by fenian on 2008-10-14
Attached is a Nautilus script (in your home directory select show hidden files fromm view menu and put it  in the .gnome2/nautilus-scripts folder and make sure its executable by right clicking choosing properties and under the permissions tab checking the make executable box ) you can than select multiple images right click and choose imageresizer and you will have a number of resizing options.

---

### Post by Sisteroot on 2008-10-18
gimp or digikam

---

### Post by Cresho on 2008-10-18
WOW!  nice recommendations guys.  I been using abc (advanced batch converter) under wine to do my picture resizing with lanczos3.  When I found that gimp uses lanczos3 for resizing, I found this to be superior than adobe photoshop.  The nautilus resize function is awsome as well while I can do resize in multible images with ctrl and selecting, I was not able to tell it what part of the picture to resize too.  I'll look at imagemagic.

Thanks!

---

### Post by bro brian on 2010-03-07
Before I ran into a problem, and had to do a clean install of Ubuntu Karmic 9.10, I used to be able to right-click on the thumb of a picture, and there was a prompt to resize. Now that I've reinstalled Karmic, I don't have that option. Does anyone know as to why?

**Actually I just found it  - The Nautilus Image Converter. Go here for post:
[http://ubuntu-tutorials.com/2007/09/17/nautilus-image-converter-quickly-resize-or-rotate-images-within-nautilus/](http://ubuntu-tutorials.com/2007/09/17/nautilus-image-converter-quickly-resize-or-rotate-images-within-nautilus/)

(And..Patrick Balleux brought this up on #3 post of this thread. I guess I didn't know at the time I posted this that the Nautilus Image Converter was the application I was needing - Ignorant as I am)

---

### Post by Kevbert on 2010-03-08
Nice package, thanks. Nautilus-image-converter is just what I wanted.

---

