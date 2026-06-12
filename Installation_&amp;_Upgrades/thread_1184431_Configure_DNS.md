---
title: "Configure DNS"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by ncnbnt on 2009-06-11
Hello again:P

well after fixing my server[Thanks to all of you] i am using plesk panel and i added my domain.

But in service Management[Module of Plesk] i see this:

[[IMG]http://imageshack.gr/files/tpbpk4b1fo9y3b6y71fh.jpg[/IMG]]("http://imageshack.gr/view.php?file=tpbpk4b1fo9y3b6y71fh.jpg")


When pressing start the same happens.

So how to configure bind to "accept my domain"?

ALSO I RUN : ```
named-g
```

And when PINGING my domain i see:



```
11-Jun-2009 08:59:06.100 client "HERE SHOWS MYIP"#35053: query (cache) 'megashare.gr/A/IN' denied
11-Jun-2009 08:59:06.633 client "MYIP"#35053: query (cache) 'megashare.gr/A/IN' denied
11-Jun-2009 08:59:17.637 client "MYIP"#35053: query (cache) 'megashare.gr/A/IN' denied
11-Jun-2009 08:59:18.361 client "MYIP"#35053: query (cache) 'megashare.gr/A/IN' denied
```


Thanks again

---

### Post by sanemanmad on 2009-06-11
hmmm... I do not know much about plesk, however I am most certain you can start by checking your logs... ```
syslog
```, ```
messages 
```etc..

---

### Post by ncnbnt on 2009-06-11
I have configured THE PLESK DNS SERVICES but the problem is in DNS.

IT DOESNT accept my domain as you see from pinging

---

### Post by ncnbnt on 2009-06-13
PLEASEEE .. . . Help. . 

Someone told me that i had to edit 2 files. . I dont know which.

Please. . 

Thanks

---

