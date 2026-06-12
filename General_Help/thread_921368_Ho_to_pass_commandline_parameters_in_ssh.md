---
title: "Ho to pass commandline parameters in ssh"
date: 2008-09-16
forum: General Help
---

### Post by kunisch on 2008-09-16
Hello

i have made a simple launcher which runs the following command:

ssh -T -l [usr] [destination]

Now this makes openssh to promt me for a password. Is there any way to define my password within the commandline enviroment, or by using <, | << or the like ?

---

### Post by Nepherte on 2008-09-16
If you want to login with ssh without ssh prompting for a password, you can setup a public/private key pair.

---

