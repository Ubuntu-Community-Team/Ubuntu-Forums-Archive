---
title: "Mirror missing files to download"
date: 2008-08-02
forum: General Help
---

### Post by AlanInVancouverBC on 2008-08-02
Some of my amd64 files are not found on a mirror in Canada. I then choose to use the main server to get these. Should that happen? I'm still pretty new to ubuntu. I'm not even sure if this is the right forum for this question. I couldn't fine another forum for this kind of issue.

---

### Post by GeordieToddy on 2008-08-03
Are the files you're after on the Main server? If so, I wouldn't worry too much. If not, what is missing?

---

### Post by AlanInVancouverBC on 2008-08-03
Here's a copy and past from the articnetwork, the server that pings best for me in Vancouver, BC, Canada

Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/main/binary-amd64/Packages.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/main/binary-amd64/Packages.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/restricted/binary-amd64/Packages.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/main/source/Sources.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/main/source/Sources.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/restricted/source/Sources.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/restricted/source/Sources.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/universe/binary-amd64/Packages.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/universe/source/Sources.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/universe/source/Sources.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/multiverse/binary-amd64/Packages.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/multiverse/source/Sources.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy/multiverse/source/Sources.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/main/binary-amd64/Packages.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/main/binary-amd64/Packages.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/restricted/binary-amd64/Packages.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/main/source/Sources.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/main/source/Sources.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/restricted/source/Sources.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/universe/binary-amd64/Packages.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/universe/source/Sources.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/universe/source/Sources.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/multiverse/binary-amd64/Packages.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 206.75.218.52 80]
Failed to fetch [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/multiverse/source/Sources.gz](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/hardy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 206.75.218.52 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I just don't get it!

---

### Post by GeordieToddy on 2008-08-03
Try changing your download server on Software Sources (try selecting main server).

System->Administration->Software Sources, under the "Ubuntu Software" tab.

Alternatively, try another Canadian Server by clicking "Server for Canada" then going to "other"

---

### Post by AlanInVancouverBC on 2008-08-03
Yes. As I stated in my first post, I can get these from the main server. My question was more: why does a mirror NOT have all the files that the main server have?

---

### Post by GeordieToddy on 2008-08-03
ah, sorry! no idea!
Does it really matter if you can use another Canadian Server?! I imagine the differences between the best ping and 2nd best ping is not that great...

---

### Post by AlanInVancouverBC on 2008-08-03
absolutely no problem. I was just considering that it would seem obvious that all mirrors (201) would have all files. That at least one doesn't strikes me as odd and wrong.
Thanks for the continuing discussion.

---

### Post by Kevbert on 2008-08-03
This seems to be a bit of a problem at the moment.  I've tried updating Intrepid from Kernel -4 to -5 and depending on which server I choose I get a different number of update files.  It may be due to some servers/pcs being down for maintenance/upgrades or just the large number of users trying to access the servers.

---

