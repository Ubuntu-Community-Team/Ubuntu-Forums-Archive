---
title: "CPU Load??"
date: 2008-09-08
forum: General Help
---

### Post by stjalsma on 2008-09-08
Just wondering if anyone can help me find out why I am getting such a heavy load on my CPU's when idle.

I am on a near fresh install of Ubuntu 8.04 so there is not much installed besides the OS.  

Running the Process Monitor shows there is nothing running that is using anywhere near how much CPU usage is going on.  I am averaging 35%-40% load.

I am on a 2 x 1.73 pentium with 2 gigs of ram.

Machine is a Gateway MT3705

Thanks in advance to anyone who has some tips on giving these cpu fans a break.

---

### Post by lakersforce on 2008-09-08
I recently opened a [[COLOR="DarkOrange"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=905730") about the same subject.

---

### Post by stjalsma on 2008-09-08
I think I figured it out.  I found a sticky that says the Process Monitor has some bugs in it.  I used "sudo apt-get install htop"

After the install run "sudo htop" and my cpu's seem to be fine.

---

