---
title: "Configure ftp to use a particular IP address"
date: 2008-11-11
forum: General Help
---

### Post by gordonsowner on 2008-11-11
Hi,

I'm using Hardy Heron in the Amazon Web Services EC2 system.  I am trying to connect from an ftp client on my EC2 box to another FTP server on the internet.  The problem is that my Ubuntu ftp client in EC2 is NATted, and has an internal (non-public routable) IP address and an external IP address which does allow direct targeting of my Ubuntu ftp client from outside the EC2 system.  I am having trouble making ftp work with the external server.  The solutions are: 1.) Use passive ftp, or 2.) configure the ftp client to use the external IP address, rather than the internal one.  Well, the ftp server does not support passive ftp, so I am trying #2.  However, I can't seem to find any documentation on forcing my ftp client (standard issue on Heron) to use a particular IP address.  Any suggestions out there?

Thanks,
matt

---

