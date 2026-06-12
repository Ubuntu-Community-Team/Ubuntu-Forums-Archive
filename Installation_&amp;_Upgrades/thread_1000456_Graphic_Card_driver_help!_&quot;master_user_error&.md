---
title: "Graphic Card driver help! &quot;master user error&quot;"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by Eremis on 2008-12-02
Hi, I am trying to install a driver for Radeon x550 graphic card. i have downloaded the driver from their website, but when I go to: Double-click the file --> run in terminal. it runs it for a while, then after 10 sec it says:"You need to run this installer as a super user" it gives me that message a couple of times, then it just stops installing. 

Any comments would be helpful 

Thanks...

PS
I have attached the error message picture

---

### Post by ajboesch on 2008-12-02
Open your terminal and type sudo su then hit enter, put in root password, now you are running as super user...

---

### Post by Eremis on 2008-12-02
i did what you said, but it only makes me root "in the terminal" so how do i run a file called "ati-driver-installer-8-11-x86.x86_64.run" using the terminal. i trued su sudo --> password --> then cd directory --> and just typed ati-driver-installer-8-11-x86.x86_64.run, but nothing happened, so what should i do?

---

### Post by Eremis on 2010-01-24
I solved this issue, here's what I did:

<cd> to the drectory where the installer was...

then: <sudo sh ati-driver-installer-8-11-x86.x86_64.run>

---

