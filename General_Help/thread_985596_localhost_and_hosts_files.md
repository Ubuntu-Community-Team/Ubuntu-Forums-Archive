---
title: "localhost and hosts files"
date: 2008-11-17
forum: General Help
---

### Post by Abstr on 2008-11-17
Okay so I have the LAMP server installed.

And I want to block websites using the Hosts file but unfortunately when I try to block a website using the following code:

```
127.0.0.1 www.example.com
```

it brings it to the LAMP homepage which would be 127.0.0.1/

So pretty much what I'm asking is how do I block a website. What code do I use? :confused:

---

### Post by dcstar on 2008-11-18
> **Abstr said:**
> Okay so I have the LAMP server installed.

And I want to block websites using the Hosts file but unfortunately when I try to block a website using the following code:

```
127.0.0.1 www.example.com
```

it brings it to the LAMP homepage which would be 127.0.0.1/

So pretty much what I'm asking is how do I block a website. What code do I use? :confused:

Define "block".

---

### Post by easoukenka on 2008-11-18
You probly want to let whoever know you are blocking a site so what about a quick text file in your web directory index.html that says this website has been blocked?

or just do 
64.233.187.99    [www.example.com](www.example.com)

which will redirect to google

---

### Post by Andrew0493 on 2009-01-04
Ya when I wanted to do this I just created an index.html file and put blocked websites. Simple as that.

---

