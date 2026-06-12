---
title: "[SOLVED] Saving Updates"
date: 2008-08-03
forum: General Help
---

### Post by pravin03 on 2008-08-03
[B][SIZE="4"][SIZE="5"]How can I save the files updated through update manager?
So that I can distribute(in CD) it to my friends who doesn't have a net connection?[/SIZE][/SIZE][/B][LEFT][/LEFT]

---

### Post by dexter.deepak on 2008-08-03
see the link in my sig.

---

### Post by ad_267 on 2008-08-03
Please just use the default font. My eyes hurt from looking at that.

You can find them in /var/cache/apt/archives or you can install the package aptoncd which gives you a gui to burn the packages to a cd.

---

### Post by pravin03 on 2008-08-03
Will this cache get cleared any time? Can I give the CD with /var/cache/apt copied to friends as complete update till now?

---

### Post by ad_267 on 2008-08-03
The cache will get cleared if you run apt-get clean. I think it should have all the updates as long as you haven't cleaned it out yourself.

---

