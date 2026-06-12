---
title: "added ram possibly not being used ?"
date: 2008-06-18
forum: Hardware
---

### Post by PhilMcRevis on 2008-06-18
I recently upgraded my laptop from 1gig (512x2) to 2 (1gx2)
The added ram shows up in the bios and ubuntu.  It is puzzling me now that I cannot get my ram usage for programs over 50% the cache seems to make use of this space.  I'm using System Monitor to watch my ram as I'm working.  If i spend all day on my laptop have firefox 3 with lots of tabs open, amarok, mysqlserver, a bunch of instances of mongrel and irb, vmware, eclipse with tomcat, etc open I still can't push past the 50%.  This is really puzzling me since that huge load of applications should be eating up a ton of memory.

Was there a config file created by the installer that is set to my previous 1 gig that I forgot to update or something?

I'm on Hardy Heron 32bit

---

### Post by sdennie on 2008-06-18
This sounds like perfectly normal behavior to me.  The average user has to try fairly hard to get linux to use more than 1G of RAM.  The fact that the cache is using most of the RAM is perfectly normal as well.  That's memory that linux is keep around so it doesn't have to go to disk for it.  You can essentially think of that RAM as a free performance boost because, if your applications actually need that RAM, linux will drop cache pages and let your applications use it.

---

### Post by stchman on 2008-06-18
> **PhilMcRevis said:**
> I recently upgraded my laptop from 1gig (512x2) to 2 (1gx2)
The added ram shows up in the bios and ubuntu.  It is puzzling me now that I cannot get my ram usage for programs over 50% the cache seems to make use of this space.  I'm using System Monitor to watch my ram as I'm working.  If i spend all day on my laptop have firefox 3 with lots of tabs open, amarok, mysqlserver, a bunch of instances of mongrel and irb, vmware, eclipse with tomcat, etc open I still can't push past the 50%.  This is really puzzling me since that huge load of applications should be eating up a ton of memory.

Was there a config file created by the installer that is set to my previous 1 gig that I forgot to update or something?

I'm on Hardy Heron 32bit

Just goes to show you that Ubuntu does not need that much RAM.  Efficient programs.

---

### Post by logos34 on 2008-06-18
If you're saying that you want it to cache less and leave it in ram instead (faster) since you've effectively doubled your memory, maybe try adjusting the **swapiness** setting.  There's a howto in the fourms somewhere.

But stchman is also right about linux being very efficient with memory management.  If you adjust it you might not see much performance improvememnt

---

### Post by sdennie on 2008-06-18
Right.  I would look at the output of:

```

free -m

```

If the bottom row (swap usage) says that no swap is being used then your system is running in an optimal fashion.  If a large amount of swap is being used, you may want to adjust swappiness as logos34 suggests.

---

