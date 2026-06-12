---
title: "Problems with Canon Lide 400 scanner and Xubuntu 20.04 desktop comp"
date: 2020-05-04
forum: Hardware
---

### Post by marsdenf on 2020-05-04
The scanner consists of two devices:

```


marsdenf@marsdenf-Z170X-Gaming-3:~$ scanimage -L
device `pixma:04A91912' is a CANON CanoScan LiDE 400 multi-function peripheral
device `escl:http://127.0.0.1:60000' is a ESCL LiDE 400 HTTP flatbed scanner
marsdenf@marsdenf-Z170X-Gaming-3:~$ 


```

  The "escl"  is the scanner's Airprint function.  The pixma device is always recognized;  sometimes the escl device is not, and I have to unplug and replug the usb connection once or a few times to get it.  The escl device always works, when it is recognized.  I have been able to scan and save images with it using simple-scan, skanlite and xsane.  (I have  installed sane-release ppa to get latest stable version of sane.)  The pixma device never works, with simple-scan the error is " Failed to scan. Unable to connect to scanner:, with skanlite: "Opening the selected scanner failed.", with xsane: "Failed to open device `pixma:04A91912': Device busy."  Can anyone help?  Should I post this on sane-projects at gitlab?

---

### Post by brian_p on 2020-05-04
What's the problem? sane-escl works for you; sane-pixma doesn't. I suppose reporting this issue on sane-devel may clarify matters.

sane-airscan is an alternative competent SANE backend to consider using:

[https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan)

---

### Post by marsdenf on 2020-05-04
What's the problem?  Well, I don't like having to plug and replug the scanner all the time.  And things should work!

---

### Post by brian_p on 2020-05-04
> **marsdenf said:**
> What's the problem?  Well, I don't like having to plug and replug the scanner all the time.  And things should work!

Indeed; I agree. Does sane-airscan perform better?

---

### Post by valmatej on 2020-05-04
I have this scanner too, I have same problem "xsane: "Failed to open device `pixma:04A91912': Device busy."

---

### Post by brian_p on 2020-05-04
> **valmatej said:**
> I have this scanner too, I have same problem "xsane: "Failed to open device `pixma:04A91912': Device busy."

But do you have the Canon Lide 400 set up in the same way as marsdenf? Otherwise, your problem is  different one and should be dealt with in a separate thread.

---

### Post by wildmanne39 on 2020-05-04
Hello and welcome to the forum valmatej, please start your own thread instead of posting in someone else's, even though the issue seems the same most of the time the cause is different and it gets confusing for the person being helped and the one doing the helping when more then one person tries to get help in a thread.

Thanks.

---

### Post by marsdenf on 2020-05-04
Sane-airscan works consistently, like sane-escl.  But it is often not recognized, like escl and unplugging/replugging is necessary.

---

### Post by brian_p on 2020-05-05
I passed your successful testing of sane-airscan to its author. He indicated that the following might help:

> ...his scanner probably goes to sleep and stops announcing itself via DNS-SD. 
+This is why discovery works unstable.                                                                                   
                                                                                                                         
May be, adding device to /etc/sane.d/airscan.conf will help him. Also he can try to tweak sleep settings in scanner      
+configuration.

---

### Post by marsdenf on 2020-05-05
I added device to /etc/sane.d/airscan.conf and also to escl.conf.   Now both escl and airscan are always recognized, no matter what I do (rebooting, shutdown/startup, unplugging, plugging etc).  So the problem is basically solved.  I sometimes get double entries for escl and airscan, and when the scanner is unplugged there is a 'ghost entry' for escl, but these don't bother me.  Pixma, which is always recognized, still doesn't work with scanner programs, but I don't really need it as escl and airscan always work.
Will now mark this thread as solved

UPDATE:  as recommended on another thread, entered  "  sudo apt remove ippusbxd  "  in a terminal and now pixma always works.  So I have removed escl and airscan entries, as they are no longer needed.

---

### Post by brian_p on 2020-05-06
Alexander Pevzner has responded with further advice:

[https://github.com/alexpevzner/sane-airscan/issues/24](https://github.com/alexpevzner/sane-airscan/issues/24)

---

### Post by jhecn on 2020-09-02
> **marsdenf said:**
> entered  "  sudo apt remove ippusbxd  "  in a terminal and now pixma always works.
Thanks for this hint. It also solved my problem even if I have a different device.

For information:
[LIST=1]
[*]In simple-scan the error was that the scanner was detected but when starting the scan I got the same error message as OP: "Failed to scan. Unable to connect to scanner"
[*]My device is : vendor=0x04a9 [Canon], product=0x1802 [TS5000 series], exact name : PIXMA TS5050
[*]I noticed the issue after the upgrade to Ubuntu 20.04.
[/LIST]

---

