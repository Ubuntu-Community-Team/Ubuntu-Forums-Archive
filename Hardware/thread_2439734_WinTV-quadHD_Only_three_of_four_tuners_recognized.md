---
title: "WinTV-quadHD: Only three of four tuners recognized"
date: 2020-03-31
forum: Hardware
---

### Post by moetteli on 2020-03-31
Hello,


The subject says it all:

[COLOR=#000000][FONT=Menlo]# ls -alh /dev/dvb/[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]total 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxr-xr-x  6 root root  120 Mar 26 01:15 [COLOR=#400bd9]**.**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxr-xr-x 19 root root 4.3K Mar 31 22:53 [COLOR=#400bd9]**..**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxr-xr-x  2 root root  120 Mar 25 20:24 [COLOR=#400bd9]**adapter0**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxr-xr-x  2 root root  120 Mar 25 20:24 [COLOR=#400bd9]**adapter1**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]drwxr-xr-x  2 root root  120 Mar 25 20:24 [COLOR=#400bd9]**adapter2**[/COLOR][/FONT][/COLOR]

This PCI-card is supposed to have 4 tuners.
The fourth tuner isn't initialized with the following errors:

[FONT=&quot]si2168 6-0064**: probe failed = -110**[/FONT]
[FONT=&quot][   15.044964] si2168**: probe of 6-0064 failed with error -110**[/FONT]
[FONT=&quot]cx23885: cx23885_dvb_register() dvb_register failed err = -22[/FONT]
[FONT=&quot][   15.045091] cx23885: cx23885_dev_setup() Failed to register dvb adapters on VID_B[/FONT]


Unfortunately, I don't know, what these error numbers mean.
Can anybody decipher this and help me?


Thanks anyway

---

