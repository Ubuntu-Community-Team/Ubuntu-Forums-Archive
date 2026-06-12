---
title: "Postfix won't send, DNS, Host or domain name not found"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by gcornelisse on 2009-03-11
I'm running all the latest packages of Intrepid.  Nothing fancy about my LAMP install.  I just apt-get upgraded recently and now my PHP apps can't send email out.  This is what I get in my logs:

```

Mar 11 18:22:26 smc-dev postfix/error[9889]: B240167C0EB: to=<gcornelisse@gmail.com>, relay=none, delay=135053, delays=135033/20/0/0.03, dsn=4.4.3, status=deferred (delivery temporarily suspended: Host or domain name not found. Name service error for name=gmail.com type=MX: Host not found, try again)

```

whois, nslookup, dig, and resolveip all give me normal results for gmail.com (its not just gmail.com I'm having trouble with)

I just can't figure out why postfix would have a problem and nothing else would....almost.  I also noticed that when I ssh into the box there is a super long "hang" before I'm given a prompt for my user/pass.  Possibly related?

Thanks,
Gary

---

### Post by fahadysf on 2009-11-10
I am having exactly the same problem on Ubuntu 8.04 server.

---

### Post by gcornelisse on 2009-11-10
I can't remember if you can do this on 8.04, but try...

dpkg-reconfigure postfix

...and select "Internet Site"

---

### Post by emaydubya on 2009-12-01
> **gcornelisse said:**
> I'm running all the latest packages of Intrepid.  Nothing fancy about my LAMP install.  I just apt-get upgraded recently and now my PHP apps can't send email out.  This is what I get in my logs:

```

Mar 11 18:22:26 smc-dev postfix/error[9889]: B240167C0EB: to=<[EMAIL="gcornelisse@gmail.com"]gcornelisse@gmail.com[/EMAIL]>, relay=none, delay=135053, delays=135033/20/0/0.03, dsn=4.4.3, status=deferred (delivery temporarily suspended: Host or domain name not found. Name service error for name=gmail.com type=MX: Host not found, try again)

```whois, nslookup, dig, and resolveip all give me normal results for gmail.com (its not just gmail.com I'm having trouble with)

I just can't figure out why postfix would have a problem and nothing else would....almost.  I also noticed that when I ssh into the box there is a super long "hang" before I'm given a prompt for my user/pass.  Possibly related?

Thanks,
Gary

I get both of these issues too.
Does the reconfig of postfix fix that?

---

