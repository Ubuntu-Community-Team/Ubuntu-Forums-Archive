---
title: "Command line: getting all files via http in a remote directory(?)"
date: 2008-11-12
forum: General Help
---

### Post by supergrover1981 on 2008-11-12
Hi gang,

Been using linux a few months, really loving at. I'm starting to migrate to command line (which I'm loving more) and wondering if there's a simple way to grab all files in a directory via http?

I'm thinking something along the lines of wget [http://www.example.com/images/*](http://www.example.com/images/*) ...but of course, wget doesn't accept regex.

Any suggestions most appreciated.

Cheers,
          - JB

---

### Post by geirha on 2008-11-12
```
man wget
``` 

The -r option makes wget grab everything recursively. You might need to tweak it further with other options.

---

### Post by supergrover1981 on 2008-11-12
*thumps head against wall*

Thanks geirha - I really should have guessed that. I missed -r in man. :-)

Cheers,
       - SuperGrover

---

