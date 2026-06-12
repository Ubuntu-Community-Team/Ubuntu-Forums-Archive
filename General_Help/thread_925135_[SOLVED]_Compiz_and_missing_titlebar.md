---
title: "[SOLVED] Compiz and missing titlebar"
date: 2008-09-20
forum: General Help
---

### Post by GNUway Tech on 2008-09-20
I installed Compiz for some nice desktop effects, and my titlebar disappeared. From what I've read, that's not uncommon. How do I get my titlebar back???

---

### Post by sayakb on 2008-09-20
Do you have emerald installed? If so, press Alt+F2 and type in:
```
emerald --replace
```

Otherwise, type in:
```
gtk-window-decorator --replace
```

Also, press Alt+f2, type in **ccsm**, click on the **Window Decoration** plugin, and change the **Command** to either of the above. Also, verify the the Window Decoration plugin is enabled.

---

### Post by GNUway Tech on 2008-09-20
Thanks, bud. Problem solved.

---

### Post by sayakb on 2008-09-20
Glad I could help! :)

---

### Post by Wolfhere on 2008-09-23
> **LinuxIsInnovation said:**
> Glad I could help! :)

I know this issue is 'resolved'. Just thought I would put my two cents worth in. I have had a very similar problem with the advent of Compiz 0.7.6.

With version 0.7.4 I had to enable in sessions compiz-decorator --replace, and emerald --replace. 

With version 0.7.6, No title bars or options within the title bar. No ability to manage windows.

In order to do that globe thingy for the sphere deformation, I had turned off the Nautilus/Preferences/Show Desktop in the Configuration Editor. I could not move any windows around or manage them. Compiz 'appeared' to be working, but without the 'windows' ability to manage windows.

Compiz --replace command at the terminal window produces the usual error. Emerald --replace has even more disastrous effects - a totally unmanaged desktop.  

Something about the installation of Compiz 0.7.6 alleviated the need for adding it to 'startup' or 'sessions' (in my growing understanding). I disabled the Compiz in Sessions along with Emerald...I rebooted and wah lah...I can use the Emerald theme manager, I can use the deforms with awesome effect and my windows have a 'close' on them..(blinds work cool too). 

Whomever it was that documented the installation of the fusion-icon is way ahead of me. Thank-you!

PS. dje Dude, you are awesome!

---

### Post by pratiks19 on 2008-10-19
> **Wolfhere said:**
> I know this issue is 'resolved'. Just thought I would put my two cents worth in. I have had a very similar problem with the advent of Compiz 0.7.6.

With version 0.7.4 I had to enable in sessions compiz-decorator --replace, and emerald --replace. 

With version 0.7.6, No title bars or options within the title bar. No ability to manage windows.

In order to do that globe thingy for the sphere deformation, I had turned off the Nautilus/Preferences/Show Desktop in the Configuration Editor. I could not move any windows around or manage them. Compiz 'appeared' to be working, but without the 'windows' ability to manage windows.

Compiz --replace command at the terminal window produces the usual error. Emerald --replace has even more disastrous effects - a totally unmanaged desktop.  

Something about the installation of Compiz 0.7.6 alleviated the need for adding it to 'startup' or 'sessions' (in my growing understanding). I disabled the Compiz in Sessions along with Emerald...I rebooted and wah lah...I can use the Emerald theme manager, I can use the deforms with awesome effect and my windows have a 'close' on them..(blinds work cool too). 

Whomever it was that documented the installation of the fusion-icon is way ahead of me. Thank-you!

PS. dje Dude, you are awesome!

can u plz explain me how to get the title bar back... i mean the startup stuff n all...

also my alt+f2 is not working after i have installed this compiz 0.7.6 and emerald

I use mac4lin theme and after doing in terminal

emerald --replace

i get the window title bar but of a different style. and after closing the terminal the title bar disappears.

and on typing this in terminal:

gtk-window-decorator --replace

i get error as:
gtk-window-decorator: symbol lookup error: gtk-window-decorator: undefined symbol: decor_blend_border_picture

---

