---
title: "Crashdump Generation Problem(ubuntu 14.04.2)"
date: 2019-08-27
forum: Hardware
---

### Post by mile1404 on 2019-08-27
Hello, I have a question about Ubuntu Crashdump.


My client uses HP DL360 Gen10 / Ubuntu 14.04.2.
However, ubuntu stop symptoms often occur. No particulars were found in the hardware log.
So I want to create a crashdump through the NMI function of HP ILO. 


I decided to test at the vmware workstation before actually applying it. 
Refer to the official Ubuntu document to proceed with Crashdump generation setup, but no dump generation and no reboot occurred.
([https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html](https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html))
 
rebooting and dump generation was not performed in ubuntu 14.04.2, 14.04.6.
ubuntu 14.04.1 was tested normally.(reboot and create dump in /var/crash) 
What's the problem?

---

### Post by mörgæs on 2019-08-28
Hi, welcome to the fora.

Is your client aware that 14.04 is out of support and contains a long list of security breaches?

---

### Post by Yellow Pasque on 2019-08-28
> **mörgæs said:**
> Is your client aware that 14.04 is out of support and contains a long list of security breaches?

Yeah, I think the client would better off with the extended support kernels: [https://ubuntu.com/support#what-is-ua](https://ubuntu.com/support#what-is-ua)

---

