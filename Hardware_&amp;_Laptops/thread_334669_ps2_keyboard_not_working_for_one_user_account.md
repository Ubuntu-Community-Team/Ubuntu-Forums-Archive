---
title: "ps/2 keyboard not working for one user account"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by bernardfrancois on 2007-01-09
Yesterday evening, I was using windows xp under vmware (running dapper). A given moment, the keyboard ceased functioning. Since I couldn't leave the vmware session without pressing Ctrl+Alt, I had to turn off my computer the hard way.

After rebooting, the keyboard worked again, untill I logged in again. When I press any key, the title bar of the window having the focus flashes.
If I look at the keyboard's settings (system > preferences > keyboard), everything seems to be fine.

When I log in as another user, I can use the keyboard again.

Maybe I should remove a hidden folder or some files files in the home directory of the user account having the problem? But which? I don't like to loose any other settngs.
And what is causing the problem?

---

### Post by bernardfrancois on 2007-01-10
I found the solution. Apparently, the *slow keys* feature got enabled somehow. I don't know how exactly that happened, but disabling it (under system>preferences>keyboard>accessibility>filters) solved the problem.

---

### Post by aln on 2007-03-11
Just run into this problem. Your solution worked like a charm :) Thanks! I'think I turned on the *slow keys * feauture by holding down Shift key while highlighting files in Konqueror. :confused: I guess I have to pay more attention to the system warnings :(

---

