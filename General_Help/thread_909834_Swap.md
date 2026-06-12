---
title: "Swap???"
date: 2008-09-03
forum: General Help
---

### Post by enzodad on 2008-09-03
i notised i have a bunch memory in swap? is there way to install ubuntu and not have that? to have it all at once and not stored away

---

### Post by zoomy942 on 2008-09-03
you mean only use RAM instead of page file?

like not having a page file?

if so - just install Ubuntu without a swap partition.  i did it like that when i first starting using ubuntu and it worked fine.  if you have application hangs, they will take longer to respond becasue thats something swap is used for.  but its up to you...

as a newer ubuntu guy - if anyone more seasoned has corrections to what i said, by all means say so - its the only way i will learn

---

### Post by iaculallad on 2008-09-03
> **enzodad said:**
> i notised i have a bunch memory in swap? is there way to install ubuntu and not have that? to have it all at once and not stored away

Try reading this [Ubuntu Swap FAQ]("https://help.ubuntu.com/community/SwapFaq").

---

### Post by mb_webguy on 2008-09-03
I'm not sure what you're asking, possibly because you may be mixing terminology.  Swap is a partition on your hard drive (which would be *storage*, not memory) that is used to temporarily store the content of your memory when your memory isn't large enough or when your computer goes into hibernation.  Your swap space should be slightly larger (about 1.5x) than your system memory.  So if you have 2GB of memory, you should have between 2GB and 3GB of swap.

---

