---
title: "How to increase the MySQL connectin Limit"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by zahidraf on 2009-04-23
Hello 

I know how to use putty etc but not expert.

I am looking script if some one help me .

I want to go to Etc folder 
Then copy the current 
my.cnf 

Then How to Edit this .

And how to save this file .

in case of any issue How i can reverse back the old file.

Thanks in advance

---

### Post by KyleBrandt on 2009-04-23
Something like (not tested): 
```
ssh fooServer "cp /etc/my.cnf /etc/my.cnf.back; sed -i '/^max_connection/ s/.*/max_connections = 200/' mysql/my.cnf"
```

This will only work if my.cnf already has a max_connections entry that is *not* commented out.  There are lots of ways to do this.

Maybe (also not tested):
```
ssh fooServer "cp /etc/my.cnf /etc/my.cnf.back; sed -i '/max_connection/ d' mysql/my.cnf; echo 'max_connections = 200' >> /etc/my.cnf
```

---

