---
title: "A way to change the desktop in the Ubuntu 10 Netbook Edition?"
date: 2010-07-16
forum: Hardware
---

### Post by HoT CuP on 2010-07-16
What packages do I remove, or what do I do to get this version of Ubuntu (10.04) to actually be productive? I can't do any draging and dropping and that sort of stuff because the desktop pseudo forces you into a certain style of setup? Basically I love this version because all the drivers work great on my netbook (Acer Aspire 532h), but I can't stand how the desktop is setup. I hook my netbook up to a monitor alot, so it don't benefit me to have everything "preorganized". Other than that, Ubuntu is awesome, and if there is no fix, it's still awesome and my favorite distro. Thanks.

---

### Post by kerry_s on 2010-07-16
you can log out & select "gnome" in the session menu to get the normal desktop.

what do you need to be productive?
everythings already on the desktop, no drag & drop needed there. favorites holds your main app's.
files & folders shows whatever you bookmark.
you can use "main menu" to add custom items.

i just got rid of gnome-panel & replaced it with awn + xcompmgr, cleaned up the launcher a little. i don't even use the full features of awn.

---

### Post by ajgreeny on 2010-07-16
On my netbook I use the standard gnome desktop, but configure it to have just a single panel instead of the normal two, and the Main menu instead of the menubar, simply to save space on the small (10.1in) screen.  It works brilliantly, and is much more friendly than the UNR desktop in my opinion.  That may, of course, be because I am so used to ubuntu's gnome desktop configured that way on my main computer.

---

### Post by HoT CuP on 2010-07-16
Thank you friends. Both answers were helpful. When I say "being productive", I don't mean it in a literal sense. I am just used to having 4 or 5 windows open at a time and draging and dropping between the windows and the desktop and it makes it really confusing with the default setup. Thanks for the answers. I see light at the end of the tunnel!

---

### Post by kerry_s on 2010-07-17
> **HoT CuP said:**
> Thank you friends. Both answers were helpful. When I say "being productive", I don't mean it in a literal sense. I am just used to having 4 or 5 windows open at a time and draging and dropping between the windows and the desktop and it makes it really confusing with the default setup. Thanks for the answers. I see light at the end of the tunnel!

i think i got you, you can turn off "single instance" so can open as many as you want with the launcher.

press-> **alt+f2**
type-> **gconf-editor**
go-> **apps-> netbook-launcher**

(if you turned it on in main menu use that)
pics:

---

### Post by HoT CuP on 2010-07-17
Yes, yes, yes! Thank you! Thank you! Thank you! That was the ol' trick o' rue. I'm feelin' it now. You feelin' it? I'm feelin it! Time for a hot cup on that note for sure. :)

---

### Post by kerry_s on 2010-07-17
> **HoT CuP said:**
> Yes, yes, yes! Thank you! Thank you! Thank you! That was the ol' trick o' rue. I'm feelin' it now. You feelin' it? I'm feelin it! Time for a hot cup on that note for sure. :)

your welcome!

you might want to try a dock(awn, cairo-dock, etc...), to replace that locked down panel.
you can use "xcompmgr" for compositing, as the standard composite does not play nice with netbook.

with awn i just middle click the task to launch another instance of the program, so i only have to use the netbook-launcher once. you can also have launchers in the dock, but i don't use that.
i have my dock on the left cause i want to get use to it, for when i switch to the new unity netbook.

with the main menu editor you can create your own launcher's even whole sections, for example: root file manager, i did a "exit options" section.

also in gconf-editor, apps-> maximus, you can black list programs you don't want maximzed.

just let me know if you need more help.

---

### Post by kerry_s on 2010-07-19
just to let you know, you can also use metacity composition as long as you turn off undecorate for maximus or it will make your panels invisible. i been using it a couple of days seems fine, so i removed xcompmgr.

---

### Post by HoT CuP on 2010-07-19
Thanks! You have been a big help. This has given me plenty of options to choose from. I think a tutorial sticky of this would help plenty of people. Thank you for being so helpful. -HoT CuP

---

