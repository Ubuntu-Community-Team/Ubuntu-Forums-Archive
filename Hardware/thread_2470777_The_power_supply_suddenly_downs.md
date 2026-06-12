---
title: "The power supply suddenly downs"
date: 2022-01-11
forum: Hardware
---

### Post by donbe1215 on 2022-01-11
I have started using Ubuntu Desktop 20.04 as a file server.

PC Spec
Xeon E3 1270 v5
32GB mem
1TB SSD
6TB HDD
300W Power Supply


During the day, I am connected via SSH and Chrome Remote Desktop.
Sometimes when I want to work and try to type a command, it is suddenly powered off.


When I checked /var/log/messages, I found the following log right after the power was turned off.
It will not reboot. It just turns off.


```

Jan 11 13:14:38 yo-PRIMERGY kernel: [ 7256.282507] [UFW BLOCK] IN=eno2 OUT= MAC=33:33:ef:c0:98:8f:a8:a1:59:35:92:b8:86:dd SRC=240f:0074:8087:0001:99c2:b06c:8acd:2150 DST=ff15:0000:0000:0000:0000:0000:efc0:988f LEN=186 TC=0 HOPLIMIT=1 FLOWLBL=553886 PROTO=UDP SPT=61895 DPT=6771 LEN=146
Jan 11 13:14:40 yo-PRIMERGY kernel: [ 7257.876730] [UFW BLOCK] IN=eno2 OUT= MAC=90:1b:0e:97:99:9d:08:10:86:43:93:90:08:00 SRC=218.253.34.134 DST=192.168.0.23 LEN=60 TOS=0x00 PREC=0x00 TTL=47 ID=56005 DF PROTO=TCP SPT=50158 DPT=8999 WINDOW=29200 RES=0x00 SYN URGP=0
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@Jan 11 13:33:17 yo-PRIMERGY kernel: [    0.000000] microcode: microcode updated early to revision 0xea, date = 2021-01-25
Jan 11 13:33:17 yo-PRIMERGY kernel: [    0.000000] Linux version 5.11.0-44-generic (buildd@lcy02-amd64-042) (gcc (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #48~20.04.2-Ubuntu SMP Tue Dec 14 15:36:44 UTC 2021 (Ubuntu 5.11.0-44.48~20.04.2-generic 5.11.22)
Jan 11 13:33:17 yo-PRIMERGY kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.11.0-44-generic root=UUID=6ebc7b5e-d65b-42a1-af35-3c1e1fdb92a4 ro quiet splash vt.handoff=7

```


Is this a hardware anomaly or something else?
I've checked ^@ and couldn't find any relevant information.
If anyone has any information on this, please let me know.

Thanks

---

### Post by Autodave on 2022-01-11
System overheating?  Fans clean?  That pretty much sounds like a bad power supply to me.....at least that is where I would start testing.

---

### Post by donbe1215 on 2022-01-11
Thanks.
The CPU temperature has settled at about 10&#8451;.
I just cleaned the fan as well.


Looking at the logs, I found some information that a BIOS update solved the problem, so I'll try that.
[https://ubuntuforums.org/showthread.php?t=2461583](https://ubuntuforums.org/showthread.php?t=2461583)

---

