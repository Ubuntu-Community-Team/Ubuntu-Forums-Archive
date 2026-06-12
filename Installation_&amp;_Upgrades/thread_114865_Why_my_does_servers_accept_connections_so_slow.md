---
title: "Why my does servers accept connections so slow?"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by robertoneto123 on 2006-01-09
Hello,

I got Ubuntu 5.04, installed sshd and proftp. Both servers works fine, but the connection takes about 15-30 seconds.

I'm on a local network, and the apache on server works fine. All the computers connects to the server using the machine's IP, so I do not believe that is something DNS-related.

The "connect to host" message cames quickly, but the "hello" after the password gets an unexpected delay.

Where can this delay came from?

Thanks

---

### Post by Kipper on 2006-01-09
All I can say is that I had the same sort of delay when using Mandrake a while ago and it was down to a bug in the ssh software. I'm sure you can run sshd in debug mode which might give you some clues as to why there is a delay in authenticating a client. I would aslo recommend you check you are using the latest versions of the ssh software. Checking the ssh config would be next on the list.

---

