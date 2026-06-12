---
title: "Failed to fetch - 404 not found"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by DarkGob on 2009-10-29
After an extended period of not using Linux, I came back to find, as one would expect, a mess of updates.  I was able to successfully download and install most of them, except for 3. The Update Manager tells me:

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2009n-0ubuntu0.9.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2009n-0ubuntu0.9.04_all.deb)
  404 Not Found [IP: 91.189.88.135 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009n-0ubuntu0.9.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009n-0ubuntu0.9.04_all.deb)
  404 Not Found [IP: 91.189.88.135 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.28-15.52_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.28-15.52_amd64.deb)
  404 Not Found [IP: 91.189.88.135 80]

But I'm able to reach that IP just fine. I expect I can just download and install these manually, but the fact that the Update Manager can't reach an IP than I can seems to be a concern. What's happening here?

---

### Post by diesch on 2009-10-29
The update manager can reach the IP but the file isn't there. Try again later or use another mirror .

---

