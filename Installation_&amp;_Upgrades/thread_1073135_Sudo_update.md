---
title: "Sudo update"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by artisan on 2009-02-18
Update manager is telling me that there is a sudo update.
When I click on the link provided I get 

"sudo (1.6.9p17-1ubuntu2.1) intrepid-security; urgency=low

  * SECURITY UPDATE: privilege escalation via non-default system groups.
    - parse.c: upstream fix for CVE-2009-0034:
      [http://www.sudo.ws/cgi-bin/cvsweb/sudo/parse.c?r1=1.160.2.21&r2=1.160.2.22](http://www.sudo.ws/cgi-bin/cvsweb/sudo/parse.c?r1=1.160.2.21&r2=1.160.2.22)

 -- Kees Cook <email address hidden>   Mon, 16 Feb 2009 12:13:47 -0800"

Can anyone explain.

---

### Post by mikewu on 2009-02-18
Reading the two links that the Changes specified, sudo had a exploit. Users with non-default groups in the sudoers file were incorrectly parsed which could lead to unauthorized privilege escalation.

Just a bug fix.

---

### Post by artisan on 2009-02-18
Thanks.
Just checking.

---

### Post by strider22 on 2009-02-25
But why is this coming from a source outside the list in sources?
It feels like a virus!

I do not have [www.sudo.ws](www.sudo.ws) in my sources list.

Version 1.6.9p10-1ubuntu3.4: 

  * SECURITY UPDATE: privilege escalation via non-default system groups.
    - parse.c: upstream fix for CVE-2009-0034:
      [http://www.sudo.ws/cgi-bin/cvsweb/sudo/parse.c?r1=1.160.2.21&r2=1.160.2.22](http://www.sudo.ws/cgi-bin/cvsweb/sudo/parse.c?r1=1.160.2.21&r2=1.160.2.22)

and the end looks like IP addresses for a different site. 

I'd like a little more explanation if possible.

---

### Post by snova on 2009-02-25
> **strider22 said:**
> But why is this coming from a source outside the list in sources?

It's not. Apt will not download from anywhere else. Run:

```
apt-cache policy sudo
```

To find a list of possible places apt would download sudo from.

> I do not have [www.sudo.ws](www.sudo.ws) in my sources list.

If you look there, it's sudo's home page. And if you look at the top of **/usr/share/doc/sudo/copyright**, you'll find confirmation.

> ```

Version 1.6.9p10-1ubuntu3.4: 

  * SECURITY UPDATE: privilege escalation via non-default system groups.
    - parse.c: upstream fix for CVE-2009-0034:
      [http://www.sudo.ws/cgi-bin/cvsweb/sudo/parse.c?r1=1.160.2.21&r2=1.160.2.22](http://www.sudo.ws/cgi-bin/cvsweb/sudo/parse.c?r1=1.160.2.21&r2=1.160.2.22)
```

and the end looks like IP addresses for a different site.

It's source code. Specifically, it's the difference between the old version and the new- the changes necessary to fix the security hole.

---

### Post by strider22 on 2009-02-25
> run apt-cache policy sudo
To find a list of possible places apt would download sudo from.

Great, Thanks, I needed that. 
I could see that [www.sudo.com](www.sudo.com) was the correct home page but with the apparent IPs at the end I wanted to check. Thanks again.

---

