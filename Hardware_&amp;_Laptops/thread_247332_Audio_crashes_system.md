---
title: "Audio crashes system???"
date: 2006-08-30
forum: Hardware &amp; Laptops
---

### Post by J-Rock! on 2006-08-30
I was having some problems with logging in.  It would hang up right after log in.  I rebooted in recovery and added a new user (non-admin) priviliges.  I was able to login fine, but had no audio.

I added my username to admin via recovery using:

adduser username admin

Then, when I tried to login again, it did the same thing as before.

I went back into /etc/group and I pinned it down to:

audio:x:29

when I remove the user from the group, I can log in fine, but no audio.  When I add the user back into the group, it hangs after login.

Any experience with this?

---

