---
title: "[SOLVED] hard drive test"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by Patriko_H on 2007-11-07
Hi all,

I have Gutsy installed on one of my machines and think I'm having problems with a bad hard drive. Is there a good non-destructive hard drive test I can run? hopefully one in the repositories?

Thx,
Patriko

---

### Post by RTrev on 2007-11-07
> **Patriko_H said:**
> Hi all,

I have Gutsy installed on one of my machines and think I'm having problems with a bad hard drive. Is there a good non-destructive hard drive test I can run? hopefully one in the repositories?

Thx,
Patriko

Steve Gibson's SpinRite is the best I know of.  It's not free, but it's worth every penny.

---

### Post by dgar on 2007-11-07
badblocks can do a non-destructive Read/Write test.  Google it.  

Be careful, it can eat your filesystem with the wrong command option. 
  ( It does warn you, I think, if you mess up )

---

### Post by Patriko_H on 2007-11-07
> **dgar said:**
> badblocks can do a non-destructive Read/Write test.  Google it.  

Be careful, it can eat your filesystem with the wrong command option. 
  ( It does warn you, I think, if you mess up )

Thanks,  I've been googling and just discovered badblocks and also that e2fsck with the proper options can non-destructively test. It appears that the FS needs to be unmounted during the test and its my root partition that's failing. I'll try this from the live CD if possible. If I don't respond for a few days you'll known why.  :-(   

Patrick

---

