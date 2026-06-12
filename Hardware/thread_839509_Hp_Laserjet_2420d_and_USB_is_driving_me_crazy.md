---
title: "Hp Laserjet 2420d and USB is driving me crazy"
date: 2008-06-24
forum: Hardware
---

### Post by solarix on 2008-06-24
Last two day's i try to get a HP Laserjet 2420d to work.
After the search in the forum i recognised that there were a lot of USB issues in the past.

The Laserjet works with Windows after a restart of the printer.

my mesage log looks like this
```

Jun 24 19:44:57 ubuntu-boxl: [  284.722681] usb 5-1: new high s                                                                                                                                                 peed USB device using ehci_hcd and address 4
Jun 24 19:44:57 ubuntu-box: [  284.855307] usb 5-1: configurat                                                                                                                                                 ion #1 chosen from 1 choice
Jun 24 19:44:57 ubuntu-box kernel: [  284.889403] usblp0: USB Bidirec                                                                                                                                                 tional printer dev 4 if 0 alt 1 proto 2 vid 0x03F0 pid 0x2917
Jun 24 19:45:03 ubuntu-box: [  290.629900] usblp0: removed
Jun 24 19:45:33 ubuntu-box: hp-toolbox(UI)[6338]: warning: Dev                                                                                                                                                 ice not found
Jun 24 19:46:03 ubuntu-box python: hp-toolbox(UI)[6338]: warning: Dev                                                                                                                                             ice not found


```

Kernel Version:

2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

```
root@ubuntu-box:~# grep disconnect /var/log/messages
Jun 19 16:29:41 ubuntu-box: [  869.810508] usb 5-1: USB disconnect, address 2
Jun 19 16:32:58 ubuntu-box: [   31.829475] usb 1-1: USB disconnect, address 2
Jun 22 13:18:13 ubuntu-box: [ 1520.872182] usb 5-1: USB disconnect, address 2
Jun 22 13:26:09 ubuntu-box: [ 1995.599014] usb 5-1: USB disconnect, address 3
Jun 22 14:32:54 ubuntu-box: [  822.977063] usb 5-1: USB disconnect, address 2
Jun 24 17:54:38 ubuntu-box: [   31.253083] usb 1-2: USB disconnect, address 2
Jun 24 18:16:24 ubuntu-box: [ 1366.179184] usb 5-2: USB disconnect, address 2
Jun 24 18:49:04 ubuntu-box: [  481.224099] usb 5-1: USB disconnect, address 2
Jun 24 18:50:11 ubuntu-box: [  548.587795] usb 5-4: USB disconnect, address 12
Jun 24 18:50:15 ubuntu-box: [  552.116789] usb 5-4: USB disconnect, address 13
Jun 24 18:50:44 ubuntu-box: [  581.207543] usb 5-4: USB disconnect, address 14
Jun 24 19:44:39 ubuntu-box: [  266.841465] usb 5-1: USB disconnect, address 2
root@aubuntu-box:~#                                                                              
```

We also have alot of -110 messages in the log.
I added the user.log as attachement with the dedicated HP Messages.

Thanks in advance for your help.

kind regards

---

