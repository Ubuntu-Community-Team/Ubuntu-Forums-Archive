---
title: "Cups Server Stuck in Processing"
date: 2012-09-14
forum: Hardware
---

### Post by nickmagus on 2012-09-14
So, I have an ubuntu server running in my apartment with CUPS on it and its all set up and I can access the administration page and everything however i am encountering a strange error. Every time I print something it prints whatever it was fine but never leaves processing the job. printing a test page from my computer 30 minutes after the page was done printing the status was still
```
processing since
Fri 14 Sep 2012 09:48:22 PM EDT 
"STS:USB MP280 00 IVFUFE 070 B 040 P 3 "
```
This processing job then prevents any other jobs from running. Canceling the job results in the next job being stuck in pending forever. cancelling the job then restarting cups clears the job properly but id rather not have to do that every time i print something. any ideas? thanks.

Note: the connected printer is a cannon pixima mp280

---

### Post by drdos2006 on 2012-09-15
Have you uninstalled and re-installed CUPS from the repository ?
Whay version of Ubuntu are you running ?

regards

---

### Post by nickmagus on 2012-09-15
yes I have and ubuntu 12.0.4.1 server

---

### Post by drdos2006 on 2012-09-15
The only thing I can think of is a mis-match between your hardware and 12.04. Whenever I have problems like that I re-install and download updates again.

Do you have the same problem if you set up server 12.04 under Virtualbox on a desktop ?

regards

---

### Post by nickmagus on 2012-09-16
Ok well I did yet another full uninstall and fresh install and it works now for some reason. i guess i must have done something wrong the first two times but im not sure what. but whatever. thanks guys

---

