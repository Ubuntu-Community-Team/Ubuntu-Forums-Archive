---
title: "Powershell - A Bash Killer?"
date: 2008-10-30
forum: General Help
---

### Post by Universal344 on 2008-10-30
I recently noticed MS released a new shell, namely [Powershell]("http://www.microsoft.com/powershell").  I downloaded it and have played with it a little bit.  Now, i wonder if for the first time ever, Microsoft will have a more powerful shell than say Bash or other Unix shells.  Its power comes from it being an object based shell.  It draws from .NET framework 2.0.  It allows for advanced management of data considering, even though it appears so, nothing that appears is just plain text (like most shells), instead everything is an object.  Not to mention, this allows for some very advanced scripting.  It is meant to replace the old cmd.exe (FINALLY!) in Windows 7 (and maybe Azure?) in its second, more improved version.  Among those improvements are a graphical user interface for it (yes, I said a gui for a shell).  It will (I think) have multiple "run spaces" and a built in text editor for Powershell scripting.  But, I don't know much on this issue and I would be more than happy to be struck down by someone with greater knowledge than me.  This thread is only meant to spark discussion.  

Also, if you've been reading around you may have heard of Microsoft [Azure]("http://microsoft.com/azure/default.aspx"), I found this very interesting.

---

### Post by ddrichardson on 2008-10-31
Please don't encourage Microsoft to send me more betas!

On one hand, its not a bad idea but its likely to become bloated and unstable, thus defeating the purpose of using the console. I'm not sure about objects though because scripts I write tend to be hacks and not in need of complex and potentially changeable design. They sure as hell wont be reusable.

I do like the drop down text completion that MS use though.

This might be better moved to the Community Cafe?

---

### Post by mixmaster on 2008-10-31
Sounds vaguely like the Workplace Shell for OS/2

---

### Post by naugiedoggie on 2008-11-02
> **Universal344 said:**
> I recently noticed MS released a new shell, namely [Powershell]("http://www.microsoft.com/powershell").  I downloaded it and have played with it a little bit.  Now, i wonder if for the first time ever, Microsoft will have a more powerful shell than say Bash or other Unix shells.  Its power comes from it being an object based shell.  It draws from .NET framework 2.0.  It allows for advanced management of data considering, even though it appears so, nothing that appears is just plain text (like most shells), instead everything is an object.  Not to mention, this allows for some very advanced scripting.  It is meant to replace the old cmd.exe (FINALLY!) in Windows 7 (and maybe Azure?) in its second, more improved version.  Among those improvements are a graphical user interface for it (yes, I said a gui for a shell).  It will (I think) have multiple "run spaces" and a built in text editor for Powershell scripting.  But, I don't know much on this issue and I would be more than happy to be struck down by someone with greater knowledge than me.  This thread is only meant to spark discussion.  

Also, if you've been reading around you may have heard of Microsoft [Azure]("http://microsoft.com/azure/default.aspx"), I found this very interesting.

Powershell 1.0 was released in Spring 2006.  Version 2 is out in beta.  However, the beta whacks quite a bit of stuff written for 1.0, so it's not a painless upgrade.  PS will be shipped with Windows 2008 server, whenever that happens.  But it still is not an OOB replacement for cmd.exe.

There actually is quite a bit of chatter among Windows sysadmins about and for PS.  Lots of scripts and tools available.  You can write your own "builtin" commands for it, either as functions loaded in a "profile" script on startup, or as plugins in C# DLLs.  

They've aliased a lot of UNIX commands to PS commands, so you can "grep" for example, or "ls" in some of the same ways you do in Cygwin.  

PS is built on top of the dotNET framework, so you can call anything in the dotNET API in a script.  For me, this has mostly been useful in using the regular expressions API and some file management stuff.  But if you have to admin Windows boxes, it is a huge improvement over cmd.exe and VBScript/WMI.  Huge.

Thanks.

mp

---

