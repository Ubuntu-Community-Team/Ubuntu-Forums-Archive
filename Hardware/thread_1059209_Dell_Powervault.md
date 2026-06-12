---
title: "Dell Powervault"
date: 2009-02-03
forum: Hardware
---

### Post by topher83 on 2009-02-03
Hi

Im new to Linux, and I've started using ubuntu 8.10.

I have a Dell powervault 110T and I don't think its being picked up

I type 
# mt -f /dev/st0 rewind
to see if it will rewind it as a test but it comes back with
mt: /dev/st0: rmtopen failed: No such file or directory

Anyone have any advise

---

### Post by cariboo on 2009-02-03
Try using sudo eg:

```
sudo mt -f /dev/st0 rewind
```

Jim

---

### Post by topher83 on 2009-02-15
No, didnt work

in /dev there is no st0 file
Dont know if that helps

My SCSI card is an adeptec 2110S and my tape drive is an dell lto2 powervault

I think if theres no st0 file then the tape drive isnt being picked up but how can i tell if the SCSI controller is there?

---

