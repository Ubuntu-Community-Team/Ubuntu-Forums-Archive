---
title: "Login screen keeps refreshing."
date: 2008-10-31
forum: General Help
---

### Post by illbashu on 2008-10-31
Like everytime i boot up, the screen constantly refreshing. like it would load up and like .5 sec later it would go away and comeback in .5 sec and it keep doing this over and over again :/ :help: is there any hope? or should i just reinstall ubuntu?

wait a min i have a separate boot partition is there a way for me to just reinstall that? what that fix it?>

---

### Post by illbashu on 2008-10-31
bump!!!!! come on someone help me!!!!

---

### Post by illbashu on 2008-10-31
Bump!

---

### Post by jstebens on 2008-10-31
Same problem. After upgrading from 8.04 to 8.10 (which should be stable now) the gdm/gdmgreeter keeps refreshing all the time, which prohibits a visual login . Havent found any suspicious entries in logfiles.

---

### Post by illbashu on 2008-11-01
i reinstalled it and it fixed the prob, but i ran into more probs so i just ended up downgradeing to hardy. I will upgrade again after a month or 2 so most of the bugs and stuff are fixed.

---

### Post by directrix on 2008-11-01
I'm having the same problem. The /var/log/syslog gets filled with Gtk-CRITICAL assertion failures:
> Nov  1 22:51:56 dx-laptop gdm[5922]: WARNING: Couldn't authenticate user
Nov  1 22:51:57 dx-laptop gdmgreeter[6369]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed
Nov  1 22:51:57 dx-laptop gdmgreeter[6369]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed
Nov  1 22:51:57 dx-laptop gdmgreeter[6369]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed
Nov  1 22:51:57 dx-laptop gdmgreeter[6369]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed
Nov  1 22:51:58 dx-laptop gdm[5922]: WARNING: Couldn't authenticate user
Nov  1 22:51:59 dx-laptop gdmgreeter[6375]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed
Nov  1 22:51:59 dx-laptop gdmgreeter[6375]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed
Nov  1 22:51:59 dx-laptop gdmgreeter[6375]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed
Nov  1 22:51:59 dx-laptop gdmgreeter[6375]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed
Nov  1 22:52:00 dx-laptop gdm[5922]: WARNING: Couldn't authenticate user

I tried using wdm, with which I was able to login and then I see the refreshing with the Ibex background :D. The sys-and Xorg logs filled with these messages:
> Nov  1 22:42:28 dx-laptop wdm: AUDIT: Sat Nov  1 22:42:28 2008: 6086 X: client 17 rejected from local host ( uid=0 gid=0 pid=5328 )
Nov  1 22:42:28 dx-laptop wdm:   Auth name: MIT-MAGIC-COOKIE-1 ID: -1
Nov  1 22:42:29 dx-laptop wdm: AUDIT: Sat Nov  1 22:42:29 2008: 6086 X: client 18 rejected from local host ( uid=0 gid=0 pid=5328 )
Nov  1 22:42:29 dx-laptop wdm:   Auth name: MIT-MAGIC-COOKIE-1 ID: -1
Nov  1 22:42:30 dx-laptop wdm: AUDIT: Sat Nov  1 22:42:30 2008: 6086 X: client 17 rejected from local host ( uid=0 gid=0 pid=5328 )
Nov  1 22:42:30 dx-laptop wdm:   Auth name: MIT-MAGIC-COOKIE-1 ID: -1
Nov  1 22:42:31 dx-laptop wdm: AUDIT: Sat Nov  1 22:42:31 2008: 6086 X: client 17 rejected from local host ( uid=0 gid=0 pid=5328 )
Nov  1 22:42:31 dx-laptop wdm:   Auth name: MIT-MAGIC-COOKIE-1 ID: -1
Nov  1 22:42:32 dx-laptop wdm: AUDIT: Sat Nov  1 22:42:32 2008: 6086 X: client 13 rejected from local host ( uid=0 gid=0 pid=5328 )
Nov  1 22:42:32 dx-laptop wdm:   Auth name: MIT-MAGIC-COOKIE-1 ID: -1

I had to fiddle with xorg.conf and reinstalling fglrx to get rid of some error messages which presumably weren't related to my big problem, because it didn't help. Ubuntu 8.04 ran without problems; although, I had to change a lot of settings to get it running properly (I've got a Dell Inspiron 6400 with a X1400 ATI card).

I'd appreciate any help I/we can get!

---

### Post by jstebens on 2008-11-03
Seems like we found something in common - I have the same MIT-MAGIC-COOKIE-1: -1  messages than you. Difference: I have an nvidia geforce 6800 GTO (nv45) and you seem to have some ATI card. Have you used envyng before on hardy?

I had the hope the new proposed beta driver updates would solve the problem - but they didnt. There seems sth else bothering the xserver.

AMD X2 4400+
Geforce 6800 GTO (nv45)
1 GB Memory
Mainboard is a Asus A8N

#dkms status
nvidia, 96.43.09, 2.6.27-7-generic, i686: installed (originale_module_exists)

starting X doesnt seem to be the problem here. I can get X up and running fine, taking mouse events. Only thing I cant get to run is a visual login - screen keeps refreshing. I have tried XDM - which lets me do a login but neither Gnome nor Xfce4 is accessible for me.

I have purged GDM completely already (including config files)

Worked fine on hardy. We might report this as a bug. Any ideas left?

---

### Post by lodman on 2008-11-03
i just installed ubuntu version 7.04, everytime i try and log in, its keeps putting zeros and wont let me put it my loggin info, please help me.

---

### Post by jstebens on 2008-11-04
> **lodman said:**
> i just installed ubuntu version 7.04, everytime i try and log in, its keeps putting zeros and wont let me put it my loggin info, please help me.

This might be the wrong thread for you. Use the search function to find a thread describing your symptoms. Also have a look at the ubuntu bug list, you might be lucky in finding the problem solved.

---

### Post by jstebens on 2008-11-04
Opened a bug report concerning this issue: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/293323](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/293323)

---

