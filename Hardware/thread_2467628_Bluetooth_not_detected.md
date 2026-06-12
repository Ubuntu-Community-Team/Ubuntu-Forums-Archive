---
title: "Bluetooth not detected"
date: 2021-10-02
forum: Hardware
---

### Post by katana-9988 on 2021-10-02
Hello. last week I have installed the latest version of KDE neon (Like Kubuntu) on my  laptop and I absolutely love it. The only thing that bugs me is that the  Bluetooth is not detected at all. I tried to search online to find a  solution but I wasn't lucky. This was the same issue even when I installed Ubuntu 21.04. 

Note : 
1 - I can assure everyone that the laptop do come with a Bluetooth built in, I was using it when I was running windows.
2 - I tried to post on KDE forums, someone did help me but we did not succeed. He asked me for a bunch of commands it only makes sense to link for the post as followed better than repeating them:-

[https://forum.kde.org/viewtopic.php?f=309&t=172762&sid=e23a29822f336452d949a62100c485be](https://forum.kde.org/viewtopic.php?f=309&t=172762&sid=e23a29822f336452d949a62100c485be)

Please advice me on what to do, I am seriously out of options.

Thanks,

---

### Post by axelmasok on 2021-10-07
Back to your laptop wifi/bluetooth.
Most/All laptops in recent years run a wifi card that also provides bluetooth functionality. I find non-Intel ones are so bad that heavy wifi use renders my bluetooth mouse useless.
So I guess the first suggestion is to research your laptop or open it up and find out what wifi card you have and check it also provides bluetooth (looks like it does, just checked - RTL8821C).

I'm guessing if you run this you get no hci0 device?

```
hciconfig
```

```
axel@axel-pc:~$ hciconfig 
hci1:   Type: Primary  Bus: USB
        BD Address: FC:F8:AE:A7:BD:B7  ACL MTU: 1021:5  SCO MTU: 96:5
        UP RUNNING 
        RX bytes:1445 acl:0 sco:0 events:173 errors:0
        TX bytes:29837 acl:0 sco:0 commands:172 errors:0

hci0:   Type: Primary  Bus: USB
        BD Address: 00:15:83:F0:ED:4C  ACL MTU: 384:8  SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:377589 acl:20126 sco:0 events:1851 errors:0
        TX bytes:1048 acl:15 sco:0 commands:50 errors:0
```

So try and get the Realtek going first. I'm guessing you have a firmware issue. See below "BlueTooth is not working" section:
[https://github.com/tomaspinho/rtl8821ce](https://github.com/tomaspinho/rtl8821ce)

Or you can bite-the-bullet like I did with my Broadcom crap wifi pcie and buy an Intel card. I found one on eeebaaaay for $10 pre loved. $10!  Works with every OS I can throw at it.

---

