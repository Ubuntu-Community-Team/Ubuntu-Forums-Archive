---
title: "Slow boot with vmware player 2.5"
date: 2008-11-12
forum: General Help
---

### Post by chrisby on 2008-11-12
My intrepid install is booting slower than I wanted I checked bootchart and it appears to be hanging with vmware-networks.

Does anyone else have this problem with vmware player 2.5 and does anyone know how to fix it?

I have attached the bootchart log

---

### Post by chrisby on 2008-11-12
Can someone tell me how to disable this vmware-networks script from starting?

---

### Post by azimout on 2009-02-04
Hi there, just came across this thread.
I have the same issue, I am looking into it now...

The vmware services start by the script /etc/init.d/vmware, and I can tell you the log is in /var/log/vnetlib...

I will post future findings here...
(according to my bootchart, I'm losing 8 seconds to vmware-networks)

---

### Post by azimout on 2009-02-04
In the log, I can see many errors like this:

VNLExtractPidFromFile - Could not open the PID file: /var/run/vmnet-netifup-vmnet1.pid, error: No such file or directory
VNLExtractPidFromFile - Could not open the PID file: /var/run/vmnet-dhcpd-vmnet8.pid, error: No such file or directory
VNLExtractPidFromFile - Could not open the PID file: /var/run/vmnet-natd-8.pid, error: No such file or directory
VNLExtractPidFromFile - Could not open the PID file: /var/run/vmnet-netifup-vmnet8.pid, error: No such file or directory
VNLExtractPidFromFile - Could not open the PID file: /var/run/vmnet-detect.pid, error: No such file or directory

Will investigate further

---

