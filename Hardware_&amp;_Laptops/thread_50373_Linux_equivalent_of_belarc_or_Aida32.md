---
title: "Linux equivalent of belarc or Aida32"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by minghai on 2005-07-20
Hi guys,

    I used to use belarc and Aida32 on Windows to get comprehensive system information.  Now that I've switched to Linux, is there an equivalent piece of software?  I know about dmesg but its not very pretty.  Thanks for any recommendations or advice.

Ming Hai

---

### Post by GeneralZod on 2005-07-20
It's not pretty, but 

```
sudo lshw -html 
```

will output formatted system info to stdout.

---

### Post by minghai on 2005-07-20
Thanks GeneralZod, that provided some info.  Have you tried Ultimate Boot CD ([http://ubcd.sourceforge.net/)?](http://ubcd.sourceforge.net/)?)  They seem to have some DOS tools like Aida16 and Astra to provide some systems info.  Of course it being DOS, I don't know how updated the tools are and whether they will detect newer hardware.

Ming Hai

---

### Post by slibuntu on 2008-05-01
Not quite as polished as belarc advisor but a way to get all that info is by running this command - 

```
sudo lshw -html >> info.html
```


This will output a file called info.html to your home directory, just open it with firefox and you should have most of the info you need!

---

