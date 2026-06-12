---
title: "LTSP problem"
date: 2005-11-08
forum: General Help
---

### Post by whiterabbit@ on 2005-11-08
Hello to all,
i have a problem setting up LTSP under Ubuntu.

That's the situation:
-i downloaded and installed ltsp packages from Synaptic and then from ltspadmin utility
-i setup dhcp and tftpd-hpa services as you can see in the attachment files
-when i boot from the client after a while the following message appears:

"
Mounting root filesystem: /opt/ltsp/i386 from:
Mounting: Unknown host
mount: nfsmount failed: no such file or directory
NFS: mount program didn't pass remote address!
Mounting root filesystem: /opt/ltsp/i386 on /mnt failed: Invalid argument
"

As you can see it seems the client doesn't receive for mount argument the IP address of the NFS server...but it's declared into dhcpd.conf file!

I'll be pleased if anyone can help..
Best regards

---

