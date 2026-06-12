---
title: "&quot;Set ccpd daemon to start automatically&quot; does not work in Ubuntu 8.04"
date: 2008-05-01
forum: Hardware
---

### Post by fyazici on 2008-05-01
I installed the latest deb drivers for Canon LBP2900 printer and worked well, but I have to start ccpd daemon manually after every booting (sudo /etc/init.d/ccpd start). For auto starting, I did:

1. sudo update-rc.d ccpd defaults 20 (failed)
2 added "captstatusui -P LBP2900 -e" to Sessions section as explained in the Canon Manual (failed)

Thanks

---

### Post by Ng Oon-Ee on 2008-06-29
Please post the output in the terminal when the above commands fail :)

---

