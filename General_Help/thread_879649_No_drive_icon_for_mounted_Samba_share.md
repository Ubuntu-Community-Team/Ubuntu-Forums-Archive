---
title: "No drive icon for mounted Samba share"
date: 2008-08-04
forum: General Help
---

### Post by negge on 2008-08-04
I tried Googling and talked with a guy on #ubuntu about a solution to this but none of them was good enough. Here's my problem:

I have a Samba share that I want to mount so that I can access it with any program, not just those that can handle network folders. I mounted the share in /etc/fstab, the line looks like this:

[quote=fstab]//10.110.3.38/Shared /media/WS09 cifs auto,credentials=/etc/credentials 0 0[/quote]

The share mounts perfectly and I can browse it from /media/WS09. However, there is no drive icon appearing on my desktop or in the Places menu. How do I get it there? Aren't all mounted items supposed to show up as a drive (I know NFS shares does...)?

---

