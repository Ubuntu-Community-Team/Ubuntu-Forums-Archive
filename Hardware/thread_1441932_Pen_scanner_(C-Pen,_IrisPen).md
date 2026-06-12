---
title: "Pen scanner (C-Pen, IrisPen?)"
date: 2010-03-29
forum: Hardware
---

### Post by phoenity123 on 2010-03-29
Hello    Does anyone use a pen scanner like C-Pen or Irispen with Ubuntu? Because I think I'll buy one of these two, but there's ofc no official linux version out.  I've read somewhere that there are two different pen-types, one sends the image to the computer and then it sends text through a special OCR program. I think this type won't work in Linux, but the other type could be working probably: it converts the image immediately to text and sends the whole text to the computer.  So, does anyone know which type will work, or does anyone use already such a pen scanner with Ubuntu?    thanks, phoenity123

---

### Post by phoenity123 on 2010-03-30
*push*  thanks for your answers, even if they're negative!  phoenity123

---

### Post by phoenity123 on 2011-05-31
*push again*

---

### Post by stian1984 on 2011-09-01
I have a (very) ugly workaround that allows me to use the C-pen with Ubuntu (or pretty much any other UNIX OS running X). I own a 3.0, but any version should work.

C-pen does not yet provide Linux support, although they now support Android devices if you own a C-pen 3.5.

By installing VirtualBox and setting up a Virtual Windows installation, getting the C-Pen to work is pretty straight forward, but how can you get the pen output to your Linux desktop?

I put together a simple Java program running in my Virtual Windows that captures text input and sends a command to the Linux host by SSH:
DISPLAY=:0 xvkbd -text 'text from c-pen' 
It works surprisingly well. and since I run VirtualBox headless with VboxHeadless, I don't ever see the Windows installation.

I'm not sure wether it even can be called a workaround, but it allows me to use the C-Pen in all my Linux applications so I guess it qualifies. 

It's of course very ineffecient and uses system resources, but when limiting the VM to only 128MB RAM, it makes very little difference on my laptop with 4GB of memory. 

VBoxHeadless is using 1-2% CPU so it's not that bad.

---

