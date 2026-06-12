---
title: "you have 1 boken package on your system!"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by seiya5 on 2009-05-11
the messege i get when trying to use update manager is the one above. 
but when i try to do it through command panel it says

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I really have no idea what is going on there. I would have thought that recoverymode would have kicked in there and then. or perhaps the best way to handle this is that. but am unaware of what exactly im looking at. 

Can you guys help me? 
            
              Thanks 
                 Seiya5

---

### Post by Partyboi2 on 2009-05-11
Hi, you can only have one package manager working at a time, check that you have not got another package manager like synaptic, dpkg, update-manager etc open at the same time.

---

### Post by WatchingThePain on 2009-05-11
Yes and I think sysnaptic can list the broken packages so that they can be removed or re-installed.

---

### Post by seiya5 on 2009-05-11
well this is what i get when i do update manager independantly. 

update manager:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.111.8_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.111.8_all.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.111.8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.111.8_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-17ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-17ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-17ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-17ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-17ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-17ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.3.9-17ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.3.9-17ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.3.9-17ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.3.9-17ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.3.9-17ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.3.9-17ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.3.9-17ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.3.9-17ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-client_1.3.9-17ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-client_1.3.9-17ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-common_1.3.9-17ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-common_1.3.9-17ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-bsd_1.3.9-17ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-bsd_1.3.9-17ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.45 80]

---

### Post by Partyboi2 on 2009-05-11
Try changing your download server under the 1st tab in Software Sources (System>Admin>Software Sources)

---

### Post by seiya5 on 2009-05-11
you know actaully what did fix it was updating first then upgrading lol

thanks guys

---

