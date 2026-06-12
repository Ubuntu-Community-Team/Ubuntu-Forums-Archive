---
title: "Add/Remove and Synaptic can't find Thunderbird in repositories??"
date: 2008-08-15
forum: General Help
---

### Post by tmhirsch65 on 2008-08-15
Hi all,

After my latest tussle with XP and malware, I bit the bullet yesterday and installed Hardy on my wife's Dell P3 laptop. I've slowly been getting things working (wireless works, yeah!:) but vid card/external monitor won't configure properly :confused:) Anyway, she doesn't like Evolution and wants her old Thunderbird back. When I run Add/Remove or Synaptic, however, I get

W: Failed to fetch [url]http://security.ubuntu.com/ubuntu/pool/main
   /t/thunderbird/thunderbird_2.0.0.14+nobinonly-0ubuntu0.8.04.1_i386.deb
  404 Not Found

Any ideas for a newbie with an impatient wife who wants to check her e-mail?

Thanks in advance.
Tom

---

### Post by iaculallad on 2008-08-15
In your terminal, try:

```
sudo apt-get update
sudo aptitude install mozilla-thunderbird
```

---

### Post by tmhirsch65 on 2008-08-15
Thanks iaculallad,

That worked! :):)

Tom

---

