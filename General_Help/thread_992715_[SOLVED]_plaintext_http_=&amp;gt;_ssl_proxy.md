---
title: "[SOLVED] plaintext http =&amp;gt; ssl proxy?"
date: 2008-11-25
forum: General Help
---

### Post by Raybdbomb on 2008-11-25
I'm looking for a solution that would allow me to mask my plaintext http traffic -- "proxy" it through an SSL enabled middle man, is this possible?

Obviously some sites don't support SSL, so I'd want to pass it from my public access computer or work computer through my ubuntu server, onto the target machine.

Anyone know how this might be accomplished?

---

### Post by tlacuache on 2008-11-25
Check [this link]("http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/") out. OpenSSH has a built in SOCKS5 proxy, so you can simply:

```
ssh -D 9999 username@ip-address-of-ssh-server
```

And then have your browser use localhost:9999 (or whatever port you chose).

You can also use tsocks in combination with the OpenSSH socks proxy to proxify almost any application. ssh as in the example above, and set up your tsocks.conf file to point to localhost 9999, then run "tsocks /path/to/application" and tsocks will do the proxying for you.

---

### Post by Raybdbomb on 2008-11-25
exactly what I was looking for.  thanks a bunch!

---

