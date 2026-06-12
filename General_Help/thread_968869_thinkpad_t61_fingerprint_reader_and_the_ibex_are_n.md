---
title: "thinkpad t61 fingerprint reader and the ibex are not jiving"
date: 2008-11-03
forum: General Help
---

### Post by tich on 2008-11-03
I recently updated from Hardy to Ibex; I was going to wait for the next long term support release but I get too excited about new Ubuntu releases!

With the distribution upgrade came a couple of nice new things and, of course, a couple of kinks that need to be ironed out.

I have a thinkpad t61 with a fingerprint reader and had no problem setting up or using the fingerprint reader with hardy (or gutsy) but for some reason it has stopped working.

To set it up i use a combination of these guides:
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Gutsy](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Gutsy)

apparently the instructions are a little bit out dated, i found this bug posting which says that it should be updated:
[https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/203973](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/203973)

everything should be working.  i can
verify my fingerprints using tf-tool --verify 
(although previously i did use the tf-tool --verify-user "user" and now i get the error message from the bug repoort) and i have inserted all the necessary pam stuff but it won't accept my fingerprint at the gdm login, when i use gksudo or when i use sudo in the terminal

any suggestions for how to fix this would be greatly appreciated!

---

### Post by tich on 2008-11-03
i found a band-aid solution and an ongoing discussion about this here:
[https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429)

there are a couple possible solutions floating around on the page, i used the one by Tom Jaeger.  search his name on the page if you need it.

i won't mark this thread as closed/solved, it isn't.  as i said this is a band-aid solution.

---

### Post by tich on 2008-11-03
i found a band-aid solution and an ongoing discussion about this here:
[https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429)

there are a couple possible solutions floating around on the page, i used the one by Tom Jaeger.  search his name on the page if you need it.

i won't mark this thread as closed/solved, it isn't.  as i said this is a band-aid solution.

---

