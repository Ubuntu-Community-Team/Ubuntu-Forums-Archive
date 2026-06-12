---
title: "[SOLVED] Compiz -&amp;gt; Desktop effects -&amp;gt; disabled -&amp;gt;now keyboard shortcuts are gone!"
date: 2008-11-14
forum: General Help
---

### Post by ee19921 on 2008-11-14
1) I want to restore all the keyboard shortcuts back to Intrepid's default. How do I do that? :confused:

2) Before, when I open firefox, it used to open maximised. Now it is not remembering the previous setting anymore. I am not sure if it is liked to what I did, though.


This is what I did to mess up.:)  Sorry for the long post!

- Last week I upgraded to 8.10. 
- A day after that I disabled the "Desktop effects" in (System Settings->Desktop -> Desktop Effects).

- Yesterday I thought to bring it back, forgetting this new location, I enabled "Desktop effects" meant for Compiz and also played around with various effects. 

- Then I realised the effects in "System Settings", I enabled it too. 

- After that I also changed the Window Manager (System Settings->Session Manager) to Compiz and change back. 

- By then I had little problems with shortcuts. So checked the keyboard shortcuts in (Sys. Set. -> Keyboard & Mouse) settings, tried to fix it. Tried out various schemes and figured KDE3 file (/usr/share/kde4/apps/kcmkeys/kde3.kksrc) had the settings I needed and imported that scheme. But even that didn't help me. 

- I disabled desktop effects for compiz and the one in System Settings. 

- Later I noticed the "Defaults" button in Keyboard shortcuts panel. So tried that. After some 100 warnings finally restored all shortcuts.

- That restored most of the shortcuts. I still have problems with it.

Alt + F2 for krunner was gone. So when I set it to "defaults" it gave me a warning that 'it is the global shortcut for "Run command"(strangely which is exactly I am modifying) and if I want to remap it'. 

alt + f3(Window operations menu) was also not working. Received the same warning msg while fixing it.

It is kinda annoying to set every shortcut. how do I restore back to default settings.

Thanks!

---

### Post by ee19921 on 2008-11-20
some how firefox problem disappeared. Now, I lost more shortcuts. :(

I have [this alt+tab problem]("http://ubuntuforums.org/showthread.php?t=960385&highlight=kubuntu+keyboard+shortcuts")

---

### Post by ee19921 on 2008-11-20
OK. I fixed it. There might be an easy way to accomplish this. 

- I created a new user. 
- logged in once to create .kde dirs
- saved my version of ~/.kde/share/config/kglobalshortcuts
- and copied over /home/[newuser]/.kde/share/config/kglobalshortcuts to my directory.
- logged in again, everything works as good as new...! phew!
- deleted the new user directories and groups


:biggrin:

---

