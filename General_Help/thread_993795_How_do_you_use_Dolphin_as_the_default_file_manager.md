---
title: "How do you use Dolphin as the default file manager in Xubuntu?"
date: 2008-11-26
forum: General Help
---

### Post by Nillerz on 2008-11-26
I'm sick of Thunar, it sucks and I hate it. I like Dolphin, it's swell.

-xubuntu 8.04
-opera 9.62

I used a cheap hack and made all folders open up in Dolphin instead of Thunar and it was sorta cool until I realized omg when I try to upload a file to the internets it used Thunar. so I uninstalled thunar. It still opened it in something veyr similar to... uh... thunar. I was like wtf. 

Then I went onto my fluxbox session and opened opera to see if it would start thunar when I try to upload an image to a website with images. It gave me some other file manager that is NOT thunar and NOT dolphin. 

I tried to get into my xfce session again but it was like "lolno" and kicked me out due to trashcan stuff. so I re-installed thunar from Fluxbox.

So, essentially, how do I install Dolphin, make it my default file manager, and make sure that when I try to upload images to the internets it uses Dolphin?

Thank you very much you clever person you.

---

### Post by kerry_s on 2008-11-26
i think your miss understanding what the difference is between the file picker used by programs and the file manager.

you do not use a file manager, when your selecting things with your browser or any other program, that's the file picker, you can use firefox's built in one by changing a about: config setting "ui.allow_platform_file_picker;false".

as for using dolphin instead of thunar, you had that right the first time just remove thunar.

---

### Post by Nillerz on 2008-11-26
Oh... um... then why does Opera in XFCE have a different file picker than Opera in Fluxbox? Can I change the file-picker?

---

### Post by Nillerz on 2008-11-26
Anyone?

---

### Post by kerry_s on 2008-11-26
> **Nillerz said:**
> Oh... um... then why does Opera in XFCE have a different file picker than Opera in Fluxbox? Can I change the file-picker?

i'm guessing xfce4 has it's own file picker and fluxbox would probably use the default X one.

the first pic is firefox in-built.
the second pic is the os version.

i'm running a custom debian lenny, using rox as the file manager.

---

### Post by Nillerz on 2008-11-29
Is there a way to change the file-picker?

---

### Post by C0NSTANTIN on 2009-06-18
> **Nillerz said:**
> I'm sick of Thunar, it sucks and I hate it. I like Dolphin, it's swell.

-xubuntu 8.04
-opera 9.62

I used a cheap hack and made all folders open up in Dolphin instead of Thunar and it was sorta cool until I realized omg when I try to upload a file to the internets it used Thunar. so I uninstalled thunar. It still opened it in something veyr similar to... uh... thunar. I was like wtf. 

Then I went onto my fluxbox session and opened opera to see if it would start thunar when I try to upload an image to a website with images. It gave me some other file manager that is NOT thunar and NOT dolphin. 

I tried to get into my xfce session again but it was like "lolno" and kicked me out due to trashcan stuff. so I re-installed thunar from Fluxbox.

So, essentially, how do I install Dolphin, make it my default file manager, and make sure that when I try to upload images to the internets it uses Dolphin?

Thank you very much you clever person you.


same issue here as well ... i wish to give up Thundar for Dolphin ...

googled to blisters for a downloading file of Dolphin or a how-to on installing Dolphin ...
i don't even know how to uninstall Thundar ... 


can you help me out with this one? pls ...

---

### Post by kerry_s on 2009-06-18
> **C0NSTANTIN said:**
> same issue here as well ... i wish to give up Thundar for Dolphin ...

googled to blisters for a downloading file of Dolphin or a how-to on installing Dolphin ...
i don't even know how to uninstall Thundar ... 


can you help me out with this one? pls ...

dolphin is in the repo, you can apt-get or use synaptic to install it.

---

### Post by MyR on 2009-06-18
I noticed you're running opera 9.62... Opera 9.64 is out and it's a bit more stable and has security updates.  I've been running 10 beta for a day or 2 and it hasn't crashed yet.
I'll post again if I find a solution to your problem.

peace

---

### Post by MyR on 2009-06-18
I did some investigation. you can try this command:
```
gconftool -s /desktop/gnome/applications/component_viewer/exec -t string "dolphin %s"
```
I'm assuming "dolphin" is the command to launch dolphin

Hope this helps

peace

---

### Post by C0NSTANTIN on 2009-06-18
lolz ... in xubuntu it was easy as getting Madonna to run semi-node on tv :D

[Applications]
        |
       \/
[Add/Remove...]


That Add/Remove is so much prompt then in Windows [i've migrated to linux for 4 days now ... 3 of witch i recovered ext4 data :P]

With "Delphin" installed .... the problem that now remains is .. "how do i get rid of Thundar" ... [i'm so not into that north gods politeistic culture ... ]

---

### Post by MyR on 2009-06-18
> **C0NSTANTIN said:**
> .... the problem that now remains is .. "how do i get rid of Thundar" ... [i'm so not into that north gods politeistic culture ... ]

same way. just uncheck the box next to thunar.

peace

---

### Post by kerry_s on 2009-06-18
> **C0NSTANTIN said:**
> lolz ... in xubuntu it was easy as getting Madonna to run semi-node on tv :D

[Applications]
        |
       \/
[Add/Remove...]


That Add/Remove is so much prompt then in Windows [i've migrated to linux for 4 days now ... 3 of witch i recovered ext4 data :P]

With "Delphin" installed .... the problem that now remains is .. "how do i get rid of Thundar" ... [i'm so not into that north gods politeistic culture ... ]

you have to leave it installed, it's dependency of xfce4, you just don't use it if you don't want to.

---

### Post by MyR on 2009-06-19
> **kerry_s said:**
> you have to leave it installed, it's dependency of xfce4, you just don't use it if you don't want to.

No we were both wrong. I just booted up my xubuntu pc and thunar is not listed in add/remove but it can be uninstalled with the command
```
sudo apt-get remove thunar
```
without otherwise affecting xfce4 in any way.

peace

---

### Post by kerry_s on 2009-06-19
> **MyR said:**
> No we were both wrong. I just booted up my xubuntu pc and thunar is not listed in add/remove but it can be uninstalled with the command
```
sudo apt-get remove thunar
```
without otherwise affecting xfce4 in any way.

peace

now open synaptic, you'll have a load of orphaned.

---

### Post by C0NSTANTIN on 2009-06-19
you guys are so great .... i am in love with this community already :X

also .... xubuntu is so much better then windows when it comes to user frendlyness, eye candy and resource imprint ... :X :X


edit1:

well ... no more Thundar :D
launched the code onto a terminal .. checked the add/remove to confirm total wipe of Thundar .... opened the Synaptics Manager and removed the 3 packs including the Xfce 4

I am thinking of confuguring "Places" panel menu since it no longer does anything ...  reinstalling Dolphin ... anything to make Dolphin rule supreme over my system :)


edit2:

same as before ... couldn't get rid of Thundar ...
when i open a Folder in Desktop, the interface is Thundar ... altough i get some kind of error when i try to open the help file...
[[IMG]http://img223.imageshack.us/img223/4551/screenshotmbb.png[/IMG]]("http://www.imagehosting.com/")

but i still don't understand why Thundar persist ... 
notice that i erasing both Thundar and Dolphin left the interface rubbed of [programs] and [locations] pop-up menus ....

from another point of view ... i have failed to make Dolphin the file manager for this system :(
more over ... i'll have to rebuild the menus since i destroyed them when i had no file manager installed ... [wanted a clean install of Dolphin ...] 

Cand someone pls help ? :-s

---

### Post by C0NSTANTIN on 2009-06-19
anyone ... pls help :-s

---

### Post by kerry_s on 2009-06-19
> **C0NSTANTIN said:**
> anyone ... pls help :-s

bummer, i told you it's part of xfce4, it all works together. it's like trying to take konqueror out of kde or explorer out of windows.
just use dolphin as a stand alone file manager.

why not just use kde if want to use dolphin and have it integrated in the desktop?

anyways, you could just rename thunar to something else and link the thunar command to dolphin, so when thunar is called it opens dolphin.

---

### Post by maddmike on 2009-06-19
Bump - wanting to dump Thunar for Filerunner.

Thanks.

---

### Post by kerry_s on 2009-06-19
> **maddmike said:**
> Bump - wanting to dump Thunar for Filerunner.

Thanks.

just leave thunar alone & use filerunner.

---

### Post by maddmike on 2009-06-19
If I click on an icon or access an application that calls a filemanager it automatically calls up Thunar - I don't want this to happen.

Option 2?

---

### Post by kerry_s on 2009-06-19
no guarantee's!

in terminal:

mkdir ~/bin
mousepad ~/bin/Thunar
put:
```
#!/bin/sh
filerunner "$@"

```

for dolphin:
```
#!/bin/sh
dolphin "$@"

```

chmod +x ~/bin/Thunar
ln -s ~/bin/Thunar ~/bin/thunar

log out and back in.

this is a per user override, it does not touch the system settings.
to use the real thunar, you have to use the full path(/usr/bin/thunar or /usr/bin/Thunar)

---

