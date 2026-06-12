---
title: "Trouble updating Ubuntu Netbook Remix"
date: 2009-03-25
forum: Hardware
---

### Post by abdel411 on 2009-03-25
For some reason, whenever I try to update my system, I get this response: 

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I'm running an Acer Aspire One, the one with the 8gb SSD. As far as I know, it's an i386 architecture, not lpia. So, where would I go to get these updates? 

When I try entering these URLs into my browser, I get 404 again. It seems that the binary-lpia folders do not exist on these servers. 

I've also tried going to different servers. It seems I have to find a way to configure synaptic so it knows my computer is an i386. 

Any thoughts?

---

### Post by snowpine on 2009-03-26
Does your Acer use the Atom processor? If so, you can use either i386 or lpia (which stands for low power intel architecture). Lpia will give you longer battery life and faster boot up, but the repositories are limited compared to i386.

I think there is a (temporary?) problem with the Hardy lpia repository. I get a similar error when I try to upgrade my Dell Mini 9 (with the factory sources.list). Sorry I don't have a better answer. :(

---

### Post by abdel411 on 2009-03-26
Thanks, that answers one question anyway. I'd never heard of lpia before, and it's good to know that I can use those packages. 

Now I guess I just have to wait for them to put lpia back up on the server. Any chance you think they've discontinued that support? That would suck, considering the technology is starting to pick up.

---

