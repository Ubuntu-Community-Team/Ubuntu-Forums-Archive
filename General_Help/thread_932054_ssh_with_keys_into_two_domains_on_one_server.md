---
title: "ssh with keys into two domains on one server"
date: 2008-09-28
forum: General Help
---

### Post by telepathetic on 2008-09-28
I've got a server and I've set up two different domains (a.com and b.com) to point to its IP.  I've generated a key pair on my local machine and put the public key in my .ssh/authorized_keys file on the server.  With all this in place, I am able to log into the server with this line 'ssh [email]user@a.com[/email]' with no password prompt.  so far so good.

Then I try to login like this 'ssh [email]user@b.com[/email]', but am getting prompted for a password.  what is going on here?  why can't I get in without the password prompt like I can with a.com?  It should be using the same key pair to authenticate.  I've triple checked that both a.com and b.com point to the same IP.

thank you so much for any help!
-telepathetic

p.s. I was asked to accept and did accept the fingerprints given for a.com and b.com on my ssh attempts, so both are in my known_hosts file, and I am no longer prompted about that.  I'm assuming that has nothing to do with my problem however.  Just mentioning it in case you were wondering.

---

### Post by telepathetic on 2008-09-28
nevermind.

I have no idea why, but it's working now.

Best I can figure the IP coming back from the DNS was flopping around still, and I just got lucky with my manual nslookups?  no idea.

---

