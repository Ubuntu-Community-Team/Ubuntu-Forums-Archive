---
title: "Need help about SSH redirection"
date: 2008-08-06
forum: General Help
---

### Post by ®om on 2008-08-06
Hi,

I have a problem with ssh remote redirection.
On a computer A, I am able to "wget 11.22.33.44", it downloads the index.html file.
From this computer, I do "ssh B -CNR3333:11.22.33.44:80"
So from B, I should be able to connect to localhost:3333 and get the index.html, but it doesn't work, I have : 
```
$ wget localhost:3333
--10:37:43--  http://localhost:3333/
  (essai: 5) => `index.html'
Connexion vers localhost|127.0.0.1|:3333... connecté.
requête HTTP transmise, en attente de la réponse... Aucune donnée reçue. //in english : "HTTP request sent, awaiting response... No data received"
Nouvel essai.

--10:37:48--  http://localhost:3333/
  (essai: 6) => `index.html'
Connexion vers localhost|127.0.0.1|:3333... connecté.
requête HTTP transmise, en attente de la réponse... Aucune donnée reçue.
Nouvel essai.

--10:37:54--  http://localhost:3333/
  (essai: 7) => `index.html'
Connexion vers localhost|127.0.0.1|:3333... connecté.
requête HTTP transmise, en attente de la réponse... Aucune donnée reçue.
Nouvel essai.
```

I am connected (Connection to ...|...|:3333... Connected), but "HTTP request sent, awaiting response... No data received"

If I use exactly the same mechanism with others servers, it works, but I have a problem with this specific one.

What's could be the problem?

---

### Post by kihjin on 2008-08-06
I tested out your configuration and it works from what I can tell.

I would say go to computer B and execute **netstat -an | grep 3333**

Try also on B **telnet localhost 3333**

and send **GET /index HTTP/1.0** followed by pressing the enter key. You might also need to send **Connection: close** for some servers...

this might help figure out why it isn't working.

Also you might want to try the same setup on computer B using the -L flag and see if you get different results. Is it possible sshd is older on that machine or not correctly configured?

Good luck!

---

### Post by ®om on 2008-08-06
Thank you for your answer :)

I resolved it (thanks to wireshark on A). I had to add an exception 11.22.33.44 to the proxy defined on A (in putty, cause A is on Windows).
The proxy blocked the SSL connection if the port was not 443.

---

### Post by kihjin on 2008-08-06
Wireshark is such a helpful tool... good that you solved it!

---

