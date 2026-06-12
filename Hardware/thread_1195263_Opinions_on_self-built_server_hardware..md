---
title: "Opinions on self-built server hardware."
date: 2009-06-23
forum: Hardware
---

### Post by adam.ec on 2009-06-23
Hi, I really need your input on selecting software and components for a self-built server system.

I'm about to deploy an Django-based intranet system which consists of around 30 users. The organisation it is for is trying to get back on it's feet after a rough downturn over the last two years and they are non-profit, so I don't have much money to spend on components.

The application will be used full time by all users and may eventually get linked to their web site to provide details from the database. It is a single Django application on top of Postgresql database. The system will also publish XML files linked from the database.

Another stumbling block I have is that the company is located in South America. Top-end or recently released components are not available locally.

So, I need to build a server for this system. I started off with a spec like this:

4GB DDR2-800 RAM
2x80GB SATAII Western Digital HD's (for the OS and Application)
2x250GB SATAII Western Digital HD's (for the database)
Either: AMD PHENOM-8650, Core2Duo E7400, or Quad Core E8200
Ubuntu 9.04 Server or Debian Lenny

Now I also looked at software RAID but this is the first time I've checked it out. It doesn't appear to support hot-swapping as it would be great if that one drive went down I could just replace it with another, which automatically backups up the working drive. I know nothing to be honest about these processes and would be grateful for advice about backup.

Some one also suggested to me that it would be better to have two basic servers, one that is redundant but is consistently backed up by the main unit. Again, which software would be used to perform this kind of operation?

Many thanks, I look forward to reading your opinions.

---

