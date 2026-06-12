---
title: "GNOME desktop won't load (blank brown screen with pointer after login)"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by authortitle on 2006-12-08
I have an old laptop on which I installed Ubuntu, initially installing Hoary via netboot (didn't have any blank CD's and wanted to see if I could, lol) and now upgraded to Edgy via Breezy and Dapper.

At some point along the upgrade path (I think Dapper?) my GNOME session has become messed up, and on logging in, nothing happens - the gdm login window dissapears, but no icons/menus appear and the usual loading splash and intro sound effect don't happen - it literally just sits at the brown desktop with a mouse pointer til I ctrl-alt-bksp. I can't be sure but I think it might have happened after trying to install beryl/aiglx/something along those lines (I know, they won't work on my laptop anyway but I was curious!)

Enlightenment and IceWM will work, so nothing can be too seriously broken. I tried creating a new user and logging in to that, with the same problem, so I don't think its in my personal config. I've seen threads with the same problem, where the solution has been to reinstall, which I'm not going to do, if only because something seemingly this simple shouldn't prompt a reinstall!

Not sure what other details to give... basically, I need a way to reinstall the default gnome session, I've played with aptitiude but not really sure which packages to alter. If anyone could advise which log files might give useful info or whatever, I'm sure that would help diagnose this.

Thanks,
Tom

---

### Post by authortitle on 2006-12-08
Sorry, could a mod move this to the appropriate forum? Thanks

---

### Post by jlintz on 2006-12-10
ah i just ran into the same problem.  everything was working fine.  then i had rebooted and i get stuck at a blank screen after logging in.  I can drop back to a shell (ctrl -alt-f1) and sudo startx and it will work fine so I know its not an xorg.conf problem.  I think its something thats being hung on the xsession startup.  There are no error messages in any log files.  Anyone know where I can see what programs are starting for my specific xsession.

---

### Post by g33knik on 2006-12-11
I don't know if this will work but it worked for me. I just want to make an attempt to in some way repay the help I have received. I had this same problem but it was a mistake I made. From the console try "sudo apt-get install ubuntu-desktop". Hope it helps.

---

### Post by COOKE on 2006-12-14
Thanks g33knik, 

I had the same issue this morning with my desktop not loading after loading some new pacakges. "sudo apt-get install ubuntu-desktop" helped get me back up and running!

COOKE

---

### Post by g33knik on 2006-12-14
Glad to hear it. :)

---

### Post by authortitle on 2006-12-19
Yep thank you g33knik, apologies I didn't reply sooner! Reinstalling ubuntu-desktop sorted it, i've switched to kubuntu desktop now anyway ;) My sound's gone AWOL but that's for another topic... cheers!

---

### Post by g33knik on 2006-12-21
My sound is gone as well. I have tried a few things from the forums. I have tried a few diagnostics and I will hear soound but not in anything else. Who knows? If I find something that works I'll let you know.:???:

---

