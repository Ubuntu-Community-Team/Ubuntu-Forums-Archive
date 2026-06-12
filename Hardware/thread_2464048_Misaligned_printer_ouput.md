---
title: "Misaligned printer ouput"
date: 2021-06-23
forum: Hardware
---

### Post by him610 on 2021-06-23
Issue: Misaligned printer output

Printer: Dell 1700N - a legacy laser printer I have owned for 13-15 years

Computer/Operating System: (Two systems)
```

hugh@h270m:~/Downloads/MFC7360N$ inxi -SMC
System:    Host: h270m Kernel: 5.8.0-53-generic x86_64 bits: 64 Desktop: Xfce 4.14.2 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASRock model: H270M-ITX/ac serial: <superuser/root required> UEFI: American Megatrends v: P2.50 
           date: 03/16/2018 
CPU:       Topology: Dual Core model: Intel Pentium G4560 bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 801 MHz min/max: 800/3500 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 801 
```
```

hugh@b450m:~$ inxi -SMC
System:    Host: b450m Kernel: 5.8.0-55-generic x86_64 bits: 64 Desktop: Xfce 4.14.2 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASRock model: B450M/ac serial: <superuser/root required> UEFI: American Megatrends v: P1.50 
           date: 10/14/2019 
CPU:       Topology: 6-Core model: AMD Ryzen 5 2600 bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 1504 MHz min/max: 1550/3400 MHz Core speeds (MHz): 1: 1451 2: 1449 3: 1476 4: 1469 5: 1377 6: 1441 7: 1377 
           8: 1375 9: 1545 10: 1544 11: 1472 12: 1377 

```

After reiinstallation of LTS 20.04.2 a few months ago including PCL printer driver for a Dell 1700N laser printer, I noticed the print output was offset beyond the left margin. There were noticeable columns on the left side of the page that were not there. 
Since I had another printer available, I postponed fixing it until a more opportune time - today was the day. I discovered I had installed the incorrect printer driver. When one goes through the CUPS setup procedure, there are several PCL drivers to choose from. Initially, I had installed driver * LJET3.PPD* which gave me the misaligned output. I corrected it by reinstalling using driver *generpcl.ppd*

In LTS 18.04, I used the generic driver for PCL5LF (for linefeed) which is no longer listed among the PCL drivers in LTS 20.04. It sort led to a guessing game. Today, during the second re-installation attempt, I noticed the *Generic PCL* drive at the bottom of the list of PCL drivers. After installing it, the printed output is properly aligned. 

Lesson learned - Take the time to install it right the first time. Consider all of the options. It will save having to go back and do it over again. Take that bone and chew on it;)

---

