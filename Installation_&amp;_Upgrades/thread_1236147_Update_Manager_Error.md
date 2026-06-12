---
title: "Update Manager Error"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by monkerz on 2009-08-10
n00b here.

Clicked Update Manager and get this error. What is it and do I need to worry. Should I remove it and how would I if I need to?

Thanks for any help you can assist with.

---

### Post by Partyboi2 on 2009-08-10
Hi, you need to add the  gpg key for that repo. to do this open a terminal (Applications>Accessories>Terminal) and add the key with
```

gpg --keyserver subkeys.pgp.net --recv-keys 9B1DB022
gpg --export --armor 9B1DB022 | sudo apt-key add -

```
then
```
 sudo apt-get update 
```

---

### Post by monkerz on 2009-08-10
:KS Worked like a charm.

I am so glad I got rid of Microsoft Windows. This was a hard adjustment, but the support forum has been a great tool to get off the ground. Thanks again.

---

