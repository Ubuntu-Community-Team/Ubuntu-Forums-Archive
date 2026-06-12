---
title: "Please help"
date: 2008-09-13
forum: General Help
---

### Post by Americanpilot923 on 2008-09-13
Ok So I'm new to Unbuntu and I was updating.. The upload stopped so I thought it was the connection. I restarted the pc and did a hard boot and I opened package manager to finish my updates and I get this message. requested operation requires superuser privilege after it tells me to put this into terminal: dpkg --configure -a     and everytime I open the package manager.. Can someone help please?!?

V/R,
Joshua

---

### Post by iaculallad on 2008-09-13
> **Americanpilot923 said:**
> Ok So I'm new to Unbuntu and I was updating.. The upload stopped so I thought it was the connection. I restarted the pc and did a hard boot and I opened package manager to finish my updates and I get this message. requested operation requires superuser privilege after it tells me to put this into terminal: dpkg --configure -a     and everytime I open the package manager.. Can someone help please?!?

V/R,
Joshua

Open your terminal (Applications->Accessories->Terminal) and just add 'sudo' on the command:

```
sudo dpkg --configure -a
```

---

### Post by Americanpilot923 on 2008-09-13
Awesome it fixed it.. Thanks!

---

