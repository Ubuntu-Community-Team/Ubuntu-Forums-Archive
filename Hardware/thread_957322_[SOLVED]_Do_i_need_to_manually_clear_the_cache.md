---
title: "[SOLVED] Do i need to manually clear the cache"
date: 2008-10-24
forum: Hardware
---

### Post by josephellengar on 2008-10-24
after I run something like puppy or gparted in RAM?

---

### Post by kpkeerthi on 2008-10-24
Which cache?

---

### Post by josephellengar on 2008-10-24
well, when I used gparted it said that it was caching 50 mb of stuff.  Do I need to manually clear that out?  Like, does it store in RAM and I need to delete it to get full use of my ram again or something?  OR does it delete when I shut down?  Thanks.

---

### Post by kpkeerthi on 2008-10-24
Don't worry about it. An unused memory is a wasted memory. It will be cleared upon shutdown or when the kernel needs to make room for other programs.
[[More]("http://www.google.com/search?q=linux%2C+where+did+all+my+memory+go")]

---

### Post by sdennie on 2008-10-24
As kpkeerthi said, there is usually no reason to clear the cache as the kernel is smart and does the what the vast majority of users would consider The Right Thing.  However, if you want to clear the cache, you can clear (most of it) with:

```

sudo sh -c "echo 1 > /proc/sys/vm/drop_caches"

```

---

