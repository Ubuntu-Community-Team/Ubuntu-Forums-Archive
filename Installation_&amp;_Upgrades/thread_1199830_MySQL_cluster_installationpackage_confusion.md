---
title: "MySQL cluster installation/package confusion"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by AwkwardSilence on 2009-06-29
I'm setting up a MySQL cluster and not sure which packages I should get and from where. I started out and installed mysql-server (meta-package to 5.0) with apt-get. Simple install and includes ndb binaries, but I found that there are some limitations with cluster v5.0 and would like to use cluster 5.1 (or higher?). There is a mysql-server-5.1 package in the repository, but it doesn't look like it has the ndb cluster binaries like 5.0 did. I started looking at the MySQL site for downloading and it is difficult to figure out what is what with the NDB cluster.

Assuming I want the latest stable version of MySQL cluster and a corresponding version of the common MySQL database (I think mysqld is required for any of the sql/query nodes?), what do I want to do?

- Install mysql-server-5.1 via apt-get and then install MySQL cluster separately? If so, from where? Is there an NDB cluster package in the Ubuntu repository now since they're separated? or install it from souce?

- Install MySQL server 5.1.35 from source and also NDB cluster 7.0.6 from source?

Side note: When installing mysql-server-5.1, why does postfix need to be configured? Are there any issues with just selecting "No configuration"?

---

