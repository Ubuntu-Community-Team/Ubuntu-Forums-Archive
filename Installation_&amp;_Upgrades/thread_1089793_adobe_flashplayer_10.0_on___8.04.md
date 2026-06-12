---
title: "adobe flashplayer 10.0 on   8.04"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by always.arvind on 2009-03-07
When I try to install adobe flash player 10 on on 8.04, I get the following error 


adobe-flashplugin: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed


I was not able to install libpango 1.20.1-1.  


Anyone has had similar issues, and got it solved?

---

### Post by zvacet on 2009-03-08
Maybe you can run

```
sudo apt-get update && sudo apt-get upgrade
```

and after that try to install adobe-flashplugin.Do you install it from **partner repo** or some other way?

---

### Post by nikislash on 2009-03-24
I had the same problem. I installed flash player 9 instead and it works fine

heres a link [http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2)

Not sure if this is the best way to solve it but i had tried a lot of other suggestions and this was the only thing that worked

---

