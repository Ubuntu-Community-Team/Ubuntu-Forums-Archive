---
title: "Home Network"
date: 2008-09-15
forum: General Help
---

### Post by anotherdisciple on 2008-09-15
Hey, I know this is an old question, but I've never been able to find an answer that I could get to work. Anywho...

I have (2) computers in my home. One is an old desktop computer (Ubuntu 8.04) that is connected to my wireless router with an Ethernet cable, the other is a laptop (Ubuntu 8.04 also) that is connected wirelessly.

I don't have a static IP... it's DHCP like most ISPs seem to give you these days.

So the question. How can I network these computers to share their home directories?

I'm supposing that the first thing I need to do is make a group (We'll call it "share" for now), put both of the computer's users in that group... Change the permissions recursively to both of the home directories to 775... Set the umask on both computers to 775 for regular users... and then the part that I don't know... what do I do after this?

Thanks in advance!

---

