---
title: "Update Manager Shows No Updates"
date: 2008-08-23
forum: General Help
---

### Post by professorchaos on 2008-08-23
I've been using the Update Manager to check for updates and for the past few weeks it's been showing nothing. Is this my problem or have there really been no updates to anything in the past few weeks?

---

### Post by overdrank on 2008-08-23
> **professorchaos said:**
> I've been using the Update Manager to check for updates and for the past few weeks it's been showing nothing. Is this my problem or have there really been no updates to anything in the past few weeks?

Hi and what version of Ubuntu are you using? Have you tried to update via the terminal ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rossjman1 on 2008-08-23
I have not recieved any updates for about a week (and a 1 package update yesterday). It just appears that not a lot of packages were updated in the repositories.

---

### Post by professorchaos on 2008-08-23
Using 8.04.1. Using the terminal doesn't yield any different results. It might just be that there've been no updates; I just thought it was an unusually long time, since before that I'd been getting them nearly every time I checked.

---

### Post by Andybr2000 on 2008-08-23
I have the same problem, no updates.
Look my post:
[http://ubuntuforums.org/showthread.php?t=894048&highlight=update+manager](http://ubuntuforums.org/showthread.php?t=894048&highlight=update+manager)

---

### Post by xSauronx on 2008-08-23
ive had the same problem for a week. i get this with apt-get:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

this is no good

---

### Post by penjuin on 2008-08-23
xSauronx,

If you are getting 404 errors, it is most likely that there is a problem on the server end. Back up your /etc/apt/sources.list and then create a new one with different servers. Perhaps a different nation like au.archive.ubuntu.com or a mirror provided by an ISP. If your only problem is 404, this should fix it.

---

### Post by Andybr2000 on 2008-08-24
I tried different servers and still have the same problem.

---

### Post by happycoder on 2008-08-24
I'm having the same issue. I've added additional information to Andybr2000's thread linked to above.

---

### Post by professorchaos on 2008-08-27
All's well; updates are back.

---

### Post by gmxgeek on 2008-08-30
> **Andybr2000 said:**
> I tried different servers and still have the same problem.

If you are using a proxy this can cause the 404 errors. Network Settings in Synaptic can set a proxy. I was getting 404 errors on an old computer at my dad's office I was working on, and it turend out to be a proxy issue.

---

