---
title: "What are the options for Legacy AMD graphics users?"
date: 2013-05-25
forum: Hardware
---

### Post by ryanch94 on 2013-05-25
I've been away from linux for about a year and have just come back, I have a Mobility Radeon HD4250 in my laptop(so I can't upgrade it). I have just installed 13.04 and have read about the proprietary drivers not supporting xorg 1.13+. Is there anything I can do to get my graphics card running properly on it, or will I have to go back to 12.04.1?

Thanks for your time :)

---

### Post by 2F4U on 2013-05-25
AMD has dropped support for all graphics cards in the HD 4xxx and below class. Therefore, with 13.04 the only driver available to you is the open source driver. You should be able to get the proprietary driver working on 12.04.

---

### Post by Mark Phelps on 2013-05-25
Make sure you install 12.04.1 -- not 12.04.2.  The newest version has the same X-server version as 12.10 and newer -- and it won't work with the legacy AMD restricted drivers.

---

