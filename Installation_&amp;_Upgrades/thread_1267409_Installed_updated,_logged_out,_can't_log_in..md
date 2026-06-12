---
title: "Installed updated, logged out, can't log in."
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by nashibuntu on 2009-09-15
Hi there.

Running Ubuntu Server 9.04. I just installed a few updates:
[LIST]
[*]man-db 2.5.5-1build1
[*]libc6 2.9-4ubuntu6.1
[*]tzdata 2009m-0ubuntu0.9.04
[*]libc6-dev 2.9-4ubuntu6.1
[*]libssl0.9.8 0.9.8g015ubuntu3.3
[*]openssl 0.9.8g-15ubuntu3.3
[/LIST]
Then I logged out, but instead of getting the login screen I got a blank screen. I can type text on it. Pressing enter just results in a new line. Tried ctrl-c. Nothing happens.

I moved to a new tty and tried logging in. No problem. Then I logged out to see if the same thing happens. It does. Only 4 tty's left.

I logged in via one of the 4 remaining tty's to check the logs. I can't see anything untoward. dpkg.log claims everything was installed successfully.

I thought about shutting down and restarting, in case that solves the problem - but then I might not be able to log in at all which would be a complete disaster.

What's the safest way to proceed?

Thank you

---

### Post by nashibuntu on 2009-09-16
No one? Perhaps a better location for this post might be the Ubuntu Server forum. If the moderator agrees, then perhaps they could move it there for me? Thank you.

---

### Post by wojox on 2009-09-16
You need to restart. I got those updates the other day as well for Jaunty Server.

---

### Post by nashibuntu on 2009-09-16
> **wojox said:**
> You need to restart. I got those updates the other day as well for Jaunty Server.

I trusted you, took the plunge and restarted and it worked. Normal login and logout has been restored. Thanks!

---

