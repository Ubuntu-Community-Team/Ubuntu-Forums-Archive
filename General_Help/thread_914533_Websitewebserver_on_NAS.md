---
title: "Website/webserver on NAS???"
date: 2008-09-08
forum: General Help
---

### Post by Predtech on 2008-09-08
Hi guys, i didn't find any real relevant info on the web so i thought i'd ask in here as i am an ubuntu user.
Ok, i just set up a freenas OS on an older shuttle pc that i used to use and put a nice little raid setup in it. I was wondering if i could set up a website and host it from the NAS?

Any help would be appreciated.

Thanks

---

### Post by ryanhaigh on 2008-09-09
I haven't used freenas but it looks like its just a BSD distro. While it already has a webserver installed for its configuration interface it might be best to install a separate one (apache/lighttpd) running on port 80 for your personal website, if you are behind a firewall/router you will need to configure port forwarding.

---

