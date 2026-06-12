---
title: "New Logo"
date: 2008-09-22
forum: General Help
---

### Post by LJ_Chaz on 2008-09-22
Hi there,

I want to change my menu icon (start-here.png). However, when I go to put a new icon in the 'places' folder, it says access is denied, as I don't have permission. How the heck do i get around this?

Thanks!

---

### Post by StOoZ on 2008-09-22
you need a super user permission.
type > sudo before any command...
go to the terminal and type :
> sudo nautilus

and then do whatever you like..

---

### Post by LJ_Chaz on 2008-09-22
Thanks mate! Is that in the terminal? Because I'm trying to just copy and paste the icon (can you tell I'm an ex-Windoze user? :P)

---

### Post by StOoZ on 2008-09-22
yes , go to the terminal , type : > sudo nautilus
and then , copy and pate to that place.

---

### Post by LJ_Chaz on 2008-09-22
Hi, thanks for that! That gave me permission which worked, however, the logo isn't changing, even after I refresh the panel (killall gnome-panel).
Any ideas??

---

### Post by Sef on 2008-09-22
> yes , go to the terminal , type :  	Quote:
 	 	 		 			 				sudo nautilus 			 		 	 	 
and then , copy and pate to that place.

That is not the correct command.  It should be ```
gksudo nautilus
```

From [Root/Sudo]("https://help.ubuntu.com/community/RootSudo"):

> You should **never** use normal sudo to start graphical applications as root. You should use gksudo  to run such programs 
For users of *Kubuntu*, use kdesu instead of gksudo. 

---

### Post by LJ_Chaz on 2008-09-22
Thanks for that! However, I still have the same problem! :)

---

### Post by StOoZ on 2008-09-22
> **Sef said:**
> That is not the correct command.  It should be ```
gksudo nautilus
```

From [Root/Sudo]("https://help.ubuntu.com/community/RootSudo"):

thanks , I didnt know that.

---

### Post by Sycron on 2008-09-22
Neither I, nice.

---

### Post by LJ_Chaz on 2008-09-22
Hi guys,
I have been at this for a couple of hours, but the logo up the top is still the same... any ideas? Thanks!

---

### Post by Sycron on 2008-09-23
Mine worked like a charm. I just don't know why you're in trouble.

---

