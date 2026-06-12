---
title: "ProFTPD wont start"
date: 2008-09-24
forum: General Help
---

### Post by Kalphak on 2008-09-24
So pro ftpd stopped working for some unknown reason. Just spontaneously stopped working for no reason. (we did re-set up the network, but that should have no effect)

I tired restarting it, but i get this error, and everytime i try to stat it from webmin normally

```
relative path not allowed in non- sections on line 177 of '/etc/proftpd/proftpd.conf'
   ...fail!
```


...halp pwease. Im a relative noob at linux...so yeah.

---

### Post by Kalphak on 2008-10-02
pleeassee? I tired reinstalling, and same problem...

---

### Post by jamesr on 2008-10-02
Hi ,

Why don't you try posting that section of the file. There seems to be problem with conf file that needs 2 blank lines at the end of the file.

---

### Post by Ed1000 on 2008-10-05
I actually have the same problem. This is the section involved

<Global>
UserAlias desktop ed
UserPassword ed 12tKxn0fbdcE6
<Directory home/ed/ftp>
</Directory>
</Global>


The line that is generating the error is the "<Directory home/ed/ftp>" line. If I counted correctly.

Any help would be appreciated

---

### Post by jamesr on 2008-10-31
Hi Folks,

Did you try adding 2 blank lines at the end of the conf file.

---

### Post by Ed1000 on 2008-11-14
Sorry, yes, that is the first thing I did. No success. Thnks for your info anyway. :-)

What apparently has helped is clearing out te cache coz it suddenly seems to work without me having done anything specific

---

