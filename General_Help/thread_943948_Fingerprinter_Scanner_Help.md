---
title: "Fingerprinter Scanner Help"
date: 2008-10-10
forum: General Help
---

### Post by Prominence on 2008-10-10
I have a HP Pavilion dv6000 with a fingerprint scanner, how do I get it to work? I heard of one driver, and tried it out, but couldn't get it to work.

---

### Post by Sam on 2008-10-10
[http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html](http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html)

---

### Post by Prominence on 2008-10-10
It says it can't find fprint_demo

---

### Post by Prominence on 2008-10-11
help?

---

### Post by Nepherte on 2008-10-11
Enable the backports repository: System > administration > software repositories

---

### Post by Sam on 2008-10-11
You must enable "universe" repository. Read [this](https://help.ubuntu.com/community/Repositories/Ubuntu).

EDIT: Oops maybe it's backport repo, according Nepherte's post.

---

### Post by Prominence on 2008-10-12
Thank you so much! It works!

---

### Post by Prominence on 2008-10-12
Well...not in the login it doesn't...what do I do?

---

### Post by Sam on 2008-10-12
Does fprint_demo regognize your fingerprint device ? Did you register your fingerprints with this tool ? Is PAM well configured ?

---

### Post by Prominence on 2008-10-12
Yeah, it asks for a scan for EVERYTHING though, I only wanted it for log in. Just kinda figured it all out.

---

