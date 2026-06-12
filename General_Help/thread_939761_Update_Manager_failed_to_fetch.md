---
title: "Update Manager failed to fetch"
date: 2008-10-06
forum: General Help
---

### Post by number3 on 2008-10-06
When I open Update Manager and click on the 'check' button I get the following error:


The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

And the details are:

Failed to fetch [http://mirrors.acm.jhu.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://mirrors.acm.jhu.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://mirrors.acm.jhu.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://mirrors.acm.jhu.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://mirrors.acm.jhu.edu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://mirrors.acm.jhu.edu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I haven't modified any settings though, so I'm not sure what would prompt this issue to appear now.

Any ideas?

---

### Post by geirha on 2008-10-06
Seems it can't find the package lists at the repository you currently are using. Until it is fixed, you can switch to the main one, or a different mirror near you from System -> Administration -> Software Sources.

---

### Post by number3 on 2008-10-06
Thanks geirha, I changed the source to 'Server for Canada' and that has resolved my problem.

Regards,

---

