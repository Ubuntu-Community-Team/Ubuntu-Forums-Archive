---
title: "New update went perfectly, but..."
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by dwhitney67 on 2009-04-26
I upgraded from 8.10 to 9.04 last weekend on one of my systems.  The other is still running 8.10.

Prior to upgrading the one system, I was able to SSH from one system to another using a shared public key, and thus not having to enter a password.

Now, however, I am unable to SSH from the 9.04 to the 8.10 without being prompted for a password.  I've regenerated a new public key to see if this would allay the problem, but it did not.  The 8.10 system is still able to SSH to the 9.04 w/o the need for me to enter a password.

Is there an incompatibility between the 9.04 and the 8.10 openssh package?

Btw, I followed the instructions [here]("http://sial.org/howto/openssh/publickey-auth/") to generate the SSH public key.

---

### Post by Triptol on 2009-04-26
Did you check your ssh config file (/etc/ssh/sshd_config)? There should be an option that enables passwordless login IIRC.

---

### Post by dwhitney67 on 2009-04-26
> **Triptol said:**
> Did you check your ssh config file (/etc/ssh/sshd_config)? There should be an option that enables passwordless login IIRC.

That's not what I want.  I want password control; I merely want passwordless access from trusted sources.

---

### Post by Triptol on 2009-04-27
You are right and I remembered wrong... I needed to turn that off, since I only wanted key based authentication. Things kinda got linked in my head :-)

Sorry can't help you anymore. I figure you've checked all your settings. Might be a bug.

---

