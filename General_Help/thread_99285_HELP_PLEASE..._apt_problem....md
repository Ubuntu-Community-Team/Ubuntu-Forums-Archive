---
title: "HELP PLEASE... apt problem..."
date: 2005-12-05
forum: General Help
---

### Post by KrisDwyer on 2005-12-05
Hi,

I SSH into my machine to get to the terminal unfortunately, as i cannot reach the repositories... 

Then i get the following Error when i try to update apt-get any help? I am behind a router, do i need to forward any ports?

---

### Post by KrisDwyer on 2005-12-05
uhh... ok my attachment didnt work.. :S

---

### Post by KermitJr on 2005-12-05
Can you ping the package site?

Can you ping google.com?

Have you activated the ethernet connection?

---

### Post by KrisDwyer on 2005-12-05
Yes... google with a 30% packet loss and the package site with 36% packet loss

EDIT: I also have my ethernet connection activated...

---

### Post by KrisDwyer on 2005-12-05
anyone willing to help me? Please? I am in dire need of the solution...

---

### Post by civic_si on 2005-12-05
i am having the same issue i think there are a couple of repositories that need to be commented out of the sources.list file.   i am going to get a new sources.list file from a fresh breezy install and replace the old one and i will let u know if that works. did u do a dist-upgrade and then the problem surfaced or did it happen all of a sudden?

---

### Post by flopsy on 2005-12-05
Strange that seveas.ubuntulinux.nl is resolving to 1.0.0.0. What does dig seveas.ubuntulinux.nl say? What about dig [www.google.com?](www.google.com?) Check /etc/resolv.conf.

You could also change sources.list to use another server.

---

### Post by KrisDwyer on 2005-12-05
Yes.... i noted it was resolving to 1.0.0.0...

Has anyone else encountered this?

---

