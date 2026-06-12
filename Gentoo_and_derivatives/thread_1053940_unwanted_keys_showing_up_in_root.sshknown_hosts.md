---
title: "unwanted keys showing up in /root/.ssh/known_hosts"
date: 2009-01-29
forum: Gentoo and derivatives
---

### Post by zapcojake on 2009-01-29
I am using Sabayon 4. As installed /root/.ssh/known_hosts has keys for 84.18.151.170, and [www.sabayonlinux.org,72.55.147.227](www.sabayonlinux.org,72.55.147.227). This has happened on both machines I am using Sabayon. Why would these keys be there? I did not put them there and Equo works with them commented out. Is there some other service that would require these keys?

---

### Post by Kinetic Being on 2009-01-29
I can't think of a reason why there would be known_keys in the root folder if you didn't put them there, unless someone else did...

I don't know much about ssh, besides shutting it down on my box, but it seems like those addresses in there could possibly login as root via ssh? Thats bad...

Do you use ssh, or did they just show up?

Make sure no one can login as root, in /etc/ssh/ssh_config (or something like that) make sure there is AllowRootLogin (or something like that) set to no.

---

### Post by zapcojake on 2009-01-29
I use ssh to administer my machines remotely.  I have an Ubuntu box and /root/.ssh/known_hosts has only the keys that it is supposed to.   This is also not default behavior in Gentoo.  I am going to post on the Sabayon site and see if they can explain it.

---

