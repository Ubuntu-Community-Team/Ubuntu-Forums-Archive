---
title: "pytick"
date: 2008-11-03
forum: General Help
---

### Post by Vangelis on 2008-11-03
Hi, after an initially unsuccessful attempt at installing pytick (well, it installed but didn't successfully display stocks), I managed to find a post which helped me successfully get it running.

However, I added it to my session applications and whenever I log out and log in again, the list of stocks that I have added in is lost and I have to re-enter them. Could someone please provide advice on how I can keep the list of stocks that pytick displays between sessions?

Thanks,

Vangelis

PS Running Ubuntu 8.10. And, loving it...

---

### Post by loomsen on 2008-11-03
locate pytick | grep -v home | grep -i readme


Should give you some info.

Where did you import it to?

I don't have this particular app running anymore, barely had... but I still got a pytickrc in my home folder

/home/me/.pytickrc

This is, btw, the default behavior of most apps, storing the local configuration in a hidden file called 

~/.<pkgname>rc

---

### Post by Vangelis on 2008-11-03
Thanks Loomsen!

I found the .pytickrc file and added the stocks manually in that file. It all works now.

Cheers,

Vangelis

---

