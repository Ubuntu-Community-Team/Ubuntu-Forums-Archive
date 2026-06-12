---
title: "Samsung repository down, any alternatives?"
date: 2013-05-30
forum: Hardware
---

### Post by Berduchwal on 2013-05-30
It appears that repository [www.bchemnet.com](www.bchemnet.com) for Samsung drivers (both scanners and printers) is down.

This thread talks about it only recently: [http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

Does anybody know any alternatives? 

Or is it just samsung.com?

---

### Post by ibjsb4 on 2013-05-30
Seems to be working now

---

### Post by Berduchwal on 2013-05-30
If it works for you then this is very strange. I can not access it. 

In Firefox I get:
```
The connection has timed out   
The server at www.bchemnet.com is taking too long to respond.
```

From the terminal:
```

W: Failed to fetch http://www.bchemnet.com/suldr/dists/debian/Release.gpg  Could not connect to www.bchemnet.com:80 (173.236.28.2). - connect (110: Connection timed out)
W: Failed to fetch http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en_GB  Unable to connect to www.bchemnet.com:http:
W: Failed to fetch http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en  Unable to connect to www.bchemnet.com:http:
W: Failed to fetch http://www.bchemnet.com/suldr/dists/debian/extra/binary-amd64/Packages  Unable to connect to www.bchemnet.com:http:
W: Failed to fetch http://www.bchemnet.com/suldr/dists/debian/extra/binary-i386/Packages  Unable to connect to www.bchemnet.com:http:

```

It has been like this for a few days now. 

The only guess I can make about the reason if it works for everybody else is that my IP is blocked?

---

### Post by ibjsb4 on 2013-05-30
This is what I see

[ATTACH=CONFIG]243267[/ATTACH]

Try another browser.

---

### Post by Berduchwal on 2013-05-30
Thanks.

My internet provider DNS not updating is at fault here. 
I can access the website on my mobile but not on my PC.

---

### Post by Pally1 on 2013-05-31
I get the same thing, [www.bchemnet.com]("http://www.bchemnet.com") is down, been like this for a week now, this is troubling. Means theres no way to get any good samsung printer drivers. Any info from them on what is happening?

---

### Post by ibjsb4 on 2013-05-31
> **Pally1 said:**
> I get the same thing, [www.bchemnet.com]("http://www.bchemnet.com") is down, been like this for a week now, this is troubling. Means theres no way to get any good samsung printer drivers. Any info from them on what is happening?

Still working here

---

### Post by Pally1 on 2013-05-31
> **ibjsb4 said:**
> Still working here

It went back to life now, dunno for how long.

---

### Post by Berduchwal on 2013-05-31
Website is fine.
I can access it via proxy. It block my IP for some reason.

---

### Post by Odur on 2013-06-01
Same here. I can't access it from my home, but everywhere else is fine.

---

### Post by MFonville on 2013-06-01
> **Odur said:**
> Same here. I can't access it from my home, but everywhere else is fine.

Here also the same. It is really irritating :-S

For the people who *can* access the website, to which IP does bchemnet.com resolve for you? Because from my home, were it is broken, it resolves to 173.236.28.2

---

### Post by Pally1 on 2013-06-03
Still down =[. I cant isntall my bloody printer because of this!!!!

---

### Post by Pally1 on 2013-06-04
Does anyone have any info on what is going on here? I sometimes can access it from my home computer, but not in the office, it wont load. Same thing with their software sources.


Is there any info on how to get to their repositories?

---

### Post by Berduchwal on 2013-06-06
Address via proxy where this topic is discussed on the site:

[http://yooproxy.com/index.php?q=http%3A%2F%2Fwww.bchemnet.com%2Fsuldr%2Fforum%2Findex.php%3Ftopic%3D132.0](http://yooproxy.com/index.php?q=http%3A%2F%2Fwww.bchemnet.com%2Fsuldr%2Fforum%2Findex.php%3Ftopic%3D132.0)

or directly:

[http://www.bchemnet.com/suldr/forum/index.php?topic=132.0](http://www.bchemnet.com/suldr/forum/index.php?topic=132.0)

Anyone who experiances the problem can help out by typing in their terminal:
```

sudo apt-get install traceroute -y
sudo traceroute -T 173.236.28.2
sudo traceroute -T 206.188.192.118
```

and posting the results in the topic via the proxy server.

---

### Post by Odur on 2013-06-08
Something has happend. I can now access the site again :)

---

