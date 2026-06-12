---
title: "portable account management"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by clarknova on 2009-09-26
I have a single system with many (~50) user accounts. I have had a problem in the past where updating Ubuntu versions, i.e., 8.10 to 9.04, caused problems and I had to reinstall fresh.

Fortunately, I had /home on its own partition and was able to keep that while formatting /.

Unfortunately, however, although I made backups of /etc/passwd, /etc/group, etc/shadow and their (-) files, I was not successful in restoring these. Or in other words, I copied my backed-up files onto the new system but ran into headaches as existing system uids and gids conflicted with those in my backup file.

I also had problems with file ownership, etc. In summary, this turned out to be a non-viable method of maintaining user accounts across a clean install.

So now I'm looking at other methods of maintaining persistent and portable account management. Would nis or ldap accomplish this for me on a single host setup? If I set up one nis or ldap and used it for local login, would I be in a better position to upgrade or format the host and then restore my nis or ldap files from a backup?

Am I going about this the right way? Anybody with experience here? It strikes me as a reasonable thing to want to do, but I haven't found any good info on it and I'm probably just not looking in the right place.

---

