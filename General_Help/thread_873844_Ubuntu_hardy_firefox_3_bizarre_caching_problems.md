---
title: "Ubuntu hardy firefox 3 bizarre caching problems"
date: 2008-07-29
forum: General Help
---

### Post by ubufrog on 2008-07-29
Hi

I am having some bizarre problems with ubuntu hardy and firefox 3. I have several issues:

1) Certain pages seem to get cached for a very long time, and it does not seem to matter how many times I clear the cache. I have tried many, many dns servers and I always get the same issue. 

2) When I put an entry in /etc/hosts that is not in the dns servers databases then I get a empty page, even though it works fine on windows firefox 3 machines (by editing hosts file in system32). Even when I copy paste a GET request (captured with ethereal) that worked on the windows machine and send it through netcat it does not arrive at the target server, but if I just send random data ( not a web request) the data arrives! I have considered that there maybe is a proxy between me and the server, but both the windows and ubuntu machines have the exact same network setup. Could it be some weird internal firefox proxy doing something it shouldn't be? I have set the firefox proxy to "no proxy", with no luck.


I know the above description is VERY vague, but I am not quiet sure how to explain this problem in more detail. Can anyone help me with this?

---

