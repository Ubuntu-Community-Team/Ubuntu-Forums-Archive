---
title: "Can I improve wine with Windows DLLs?"
date: 2008-11-08
forum: General Help
---

### Post by Znupi on 2008-11-08
Say I have a copy of Windows and I can get all the DLLs from it. Can I improve my wine installation with them? How?

---

### Post by DGortze380 on 2008-11-08
> **Znupi said:**
> Say I have a copy of Windows and I can get all the DLLs from it. Can I improve my wine installation with them? How?

depends on what you're trying to run. just adding a bunch of .DLLs won't help anything. If you need a particular .DLL, then you can certainly install it in wine.

---

### Post by Znupi on 2008-11-08
> **DGortze380 said:**
> depends on what you're trying to run. just adding a bunch of .DLLs won't help anything. If you need a particular .DLL, then you can certainly install it in wine.
Paint.NET. I'm currently running it in a Virtual Machine using VBox and it works perfectly, but the virtual machine is a bit slow. I installed dotnet20 using winetricks and the program starts, but it isn't usable at all. I don't know which DLL's I'd have to use. I was hoping there would be a way to import all / most of the Windows DLLs if you had them (they can't be larger than 700MB, right?) and this way you'd probably get a lot better performance and compatibility.
Maybe I should ask the developer of Paint.NET what DLLs it uses? Is there some way to find out in Windows?

---

### Post by mpascall on 2008-11-10
I was just wondering the same thing.  I don't know much about wine and how it works, but I did remember hearing you could use real DLL's.  It occurred to me that if I just loaded all of the DLLs from my XP boot drive, then Wine should run great!

I did a google search "wine windows dll" to see if I could figure out how to do this, and in the first result ([http://www.codeweavers.com/support/docs/wine-user/config-dll]("http://www.codeweavers.com/support/docs/wine-user/config-dll")), it says "If your programs don't work as expected, then it's often because one DLL or another is failing. This can often be resolved by changing certain DLLs from Wine built-in to native Windows DLL file and vice versa."

The website also has a chart showing which DLLs you should definitely NOT over-ride: kernal, kernal32, user, user32, gdi, and gdi32.  And it later goes on to list the DLLs that come with Wine and comment on what they're used for and whether its a good idea to replace or not.  You can probably use this to guess which DLL's your app references.  But keep in mind replacing one might cause more problems.  So you should probably try replacing them one at a time.  Here are the DLL's they list as safe to replace:

commdlg, comdlg32
commctrl, comctl32
shell, shell32
crtdll
dplay, dplayx
msvideo, msvfw32
mciavi.drv

[URL="http://www.winehq.org/site/docs/wineusr-guide/config-wine-main"]
http://www.winehq.org/site/docs/wineusr-guide/config-wine-main[/URL] explains how to replace DLL's and some other tips.  

Hope that helps you!
-M

---

### Post by Znupi on 2008-11-10
That's very helpful! Thanks a lot! :)

---

