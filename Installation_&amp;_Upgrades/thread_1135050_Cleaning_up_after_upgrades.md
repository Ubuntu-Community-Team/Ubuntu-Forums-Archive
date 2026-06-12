---
title: "Cleaning up after upgrades?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by gabello on 2009-04-24
Hi, I'm just upgrading from 8.04 to 9.04 using the Distribution Upgrade option (thus installing 8.10 also). Since I'm quite limited in HDD space allocated to Ubuntu (I installed it first using wubi and I'm on a dual boot machine) I want to know what cleaning procedures I need to do after I install 8.10 (or 9.04) in order to remove all the unused installations files.

Thank you

---

### Post by mcduck on 2009-04-24
"sudo apt-get clean". This will remove all apt's cached package files. That's pretty much all you need to do. :)

---

