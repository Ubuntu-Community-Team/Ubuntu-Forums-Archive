---
title: "[SOLVED] can't start firefox without sudo"
date: 2008-11-24
forum: General Help
---

### Post by gilli4 on 2008-11-24
Hi everyone,

I had a seach on the forums, please excuse if this post is redundant.
Since a couple of days I've set up Ubuntu Studio 8.10 on my notebook and I'm configuring it slowly.

I can't seem to start Firefox without sudo rights. For instance, if I try to start FF via Gnome Do, I'll see it in the taskbar with a title much like "Firefox is starting..", and then it just vanishes. Neither it will start, if I try it from a shell *without* being sudo. Only if I start it as sudo, it'll do for me.

Now I know that I was able to add/remove programs without sudo rights on my current system earlier. This somehow is also affected by the above mentioned problem now. So now, if I want to add/remove programs, I'll either have to start "sudo synaptic" from a shell or I'll have to start "sudo gnome-app-install".

Whenever I try to start one of the applications in the shell without being sudo, I'll get the common error message "No protocol specified - Could not open display 0:0".

I'm very new to Linux but if there's any additional info needed, I'll be glad to find it out and write it down here.

Thanks in advance for any help.

---

### Post by ChanServ on 2008-11-24
you .mozzila dir in ~ is probably causing the problem.  deleting it will reset all the settings for firefox and then a new one will be created when you start firefox again as a user.

edit: or you can copy the one you are useing when you run firefox as root. it is in /root/.mozilla

---

### Post by sirjoebob on 2008-11-24
Could just be that you don't have permission to the ,mozilla directory. You could check by issuing "gksudo nautilus" at terminal and browsing to the /home/YOURUSERNAME/

hit ctrl+h to show hidden files and right click on .mozilla and go to propoerties. Check what your permissions are on the dir.

---

### Post by gilli4 on 2008-11-25
Both answers were very helpful. On the one hand because I can see the root of the problem now and on the other hand because I got to know the binary name of the default file explorer and its shortcut to see hidden files. Thank you both so much!

Indeed it was because of the '~<user>/.mozilla' directory.
Fortunately I didn't have to delete it, just made a chmod a+rwx to make it accessible for all groups and then, when I started FF without root rights, it asked me to create a profile for the first time. For anyone encountering the same problem:
You'll have to set the rights for the subdirectories (at least '.mozilla/firefox') as well to be sure your profile can be created in there.

The other problem I had mentioned (about the need of sudo to add/remove programs) can be fixed by setting the rights for the file  '~<user>/.Xauthority'. It's strange, I had also encountered access problems to that file on Kubuntu earlier.

How can I set this thread to [solved] ?
edit: found the thread options on top of the page :)

---

