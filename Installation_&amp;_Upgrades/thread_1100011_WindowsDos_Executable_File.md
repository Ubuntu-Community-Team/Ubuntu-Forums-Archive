---
title: "Windows/Dos Executable File?"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by Ajak25 on 2009-03-18
I know about Wine and I've got that all installed right. But I was wondering if anyone knew of an application for Ubuntu that would allow me to run Windows/Dos Executable files. Take for instance, a Warcraft 3 Auto Refresher. (This is used to refresh the slots while hosting a game on Battle.net) I have one on my desktop, but am unable to run it with Wine and I can't seem to find an Ubuntu compatible refresher online. Send me an email or just post below me, any ideas you have to this problem. I'm pretty sure I've heard of a program that could run these files but I'm not sure o.O. 

PS: Sorry if I'm posting in the wrong place heh.

---

### Post by Mark Phelps on 2009-03-19
> **Ajak25 said:**
> I know about Wine and I've got that all installed right. But I was wondering if anyone knew of an application for Ubuntu that would allow me to run Windows/Dos Executable files. 

Yes -- Wine!!

Linux is not MS Windows -- it doesn't understand .EXE files.  Wine provides a SW layer that DOES understand .EXE files. 

There are variations on Wine that provide more capabilities, but as far as I know, they're all published by CodeWeavers.

So, basically, it's Wine, or one of it's variants.

---

### Post by Elisavan on 2009-08-29
> **Mark Phelps said:**
> Yes -- Wine!!

Linux is not MS Windows -- it doesn't understand .EXE files.  Wine provides a SW layer that DOES understand .EXE files. 

There are variations on Wine that provide more capabilities, but as far as I know, they're all published by CodeWeavers.

So, basically, it's Wine, or one of it's variants.

((I know this thread doesn't have good tags that relate to my issue, but I figured that since this thread contained half of my answer already, I shouldn't go creating more threads and needless clutter on the nice, pretty site ^_~*))

So, if I wanted to run, for instance, an[COLOR=Red] .EXE[/COLOR] file with Type: *"DOS/Windows executable (application/x-ms-dos-executable)"*, [COLOR=Red]Wine[/COLOR] would be my best (if not only) choice?

I have a CDRom I need to be able to run for one of my classes, and I'd prefer it if I didn't have to rely on my roomate's [COLOR=Blue]Vista[/COLOR] laptop every time *Resists strong urge to shudder*

---

### Post by DirtDawg on 2009-08-29
> **Elisavan said:**
> ((I know this thread doesn't have good tags that relate to my issue, but I figured that since this thread contained half of my answer already, I shouldn't go creating more threads and needless clutter on the nice, pretty site ^_~*))

So, if I wanted to run, for instance, an[COLOR=Red] .EXE[/COLOR] file with Type: *"DOS/Windows executable (application/x-ms-dos-executable)"*, [COLOR=Red]Wine[/COLOR] would be my best (if not only) choice?

I have a CDRom I need to be able to run for one of my classes, and I'd prefer it if I didn't have to rely on my roomate's [COLOR=Blue]Vista[/COLOR] laptop every time *Resists strong urge to shudder*

Yes, Wine is your best bet. Try running your EXE file. The worst that could happen is it doesn't work.

If it doesn't run, try running wine from a terminal. That way you'll get some error messages that may (or may not) help you run your program.

---

### Post by mikewhatever on 2009-08-30
Hi Elisavan, I think running Windows in Virtual box is also an option, and the result is usually quite a success.

---

