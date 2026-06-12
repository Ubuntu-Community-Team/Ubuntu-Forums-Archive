---
title: "How can I find my exteral IP address"
date: 2008-07-22
forum: General Help
---

### Post by uberlube on 2008-07-22
Just like the title says. I want to connect to my home SSH while I'm on a road trip.

---

### Post by Yuki_Nagato on 2008-07-22
_[http://whatismyip.com/]("http://whatismyip.com/")_

It screams it back at you.

---

Just to be sure, you have your SSH port forwarded if you are using a router?

---

### Post by iaculallad on 2008-07-22
> **uberlube said:**
> Just like the title says. I want to connect to my home SSH while I'm on a road trip.

Using checkip.dyndns.org to get your external IP address:

```
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

---

### Post by Joeb454 on 2008-07-22
I think whatismyip may be the easier option...the terminal command is the cooler option though :)

---

### Post by Separ on 2008-07-22
Make sure you have a static external IP and if not, run something like noip2 or dyndns.

[http://ipchicken.com](http://ipchicken.com) also screams it back at you.

---

### Post by FluffyElmo on 2008-07-22
Some ISPs change IP addresses frequently. If that is the case and you want to connect from the road then you have to set up dynamic dns: [https://help.ubuntu.com/community/DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS")

It depends on your ISP though. I've found that DSL providers change IP addresses fairly frequently while Cable providers tend to be stable. Wouldn't hurt to set up Dynamic DNS anyways, it works whether the IP changes or not:)

---

### Post by uberlube on 2008-07-22
Thanks all that was quick :)

---

### Post by Joeb454 on 2008-07-22
There's no need to thank EVERYBODY ;) Though I'm sure they won't complain.

---

### Post by uberlube on 2008-07-22
Well everybody gave good advice :) 1 more question though. I have made my account at dyndns and set up a host within and entered the proper info into my router. DynamicDNS is activated now but I cant connect to my server with the host address that dyndns gave me, it just times out. Can I not log in this way while Im connected to my home network? Is it just my internal IP that will work while Im on the same router?

---

### Post by Yuki_Nagato on 2008-07-23
I am currently combating this same problem.  The ISP keeps swapping my IP address.  I will pick you back up when I solve my problem.

---

