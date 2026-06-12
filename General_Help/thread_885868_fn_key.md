---
title: "fn key"
date: 2008-08-10
forum: General Help
---

### Post by Nabeel Ali on 2008-08-10
How to activate fn key in ubuntu 8.04

---

### Post by TenPlus1 on 2008-08-10
The fn key should be a laptop only key and not recognised by the software itself...  As far as I'm aware your laptop will detect the key and the fn-function pressed and that should be recognised itself, volume/contrast/brightness/volume...

---

### Post by Nabeel Ali on 2008-08-10
my laptop is hp pavilion dv2000, fn key is not working (I can't use any function by fn key)

---

### Post by bondik on 2008-09-27
> **Nabeel Ali said:**
> my laptop is hp pavilion dv2000, fn key is not working (I can't use any function by fn key)

I suggest to verify that pressing FN keys (like FN-Mail,...) creates log record in "/var/log/acpid". For example pressing my FN-Mail key (on asus) generates  following acpi log:

```

[Sat Sep 27 21:05:13 2008] received event "hotkey ATKD 00000050 00000000"
[Sat Sep 27 21:05:13 2008] notifying client 6283[111:123]
[Sat Sep 27 21:05:13 2008] notifying client 6482[0:0]
[Sat Sep 27 21:05:13 2008] notifying client 6482[0:0]
[Sat Sep 27 21:05:13 2008] executing action "/etc/acpi/mailbtn.sh"
[Sat Sep 27 21:05:13 2008] BEGIN HANDLER MESSAGES
[Sat Sep 27 21:05:13 2008] END HANDLER MESSAGES
[Sat Sep 27 21:05:13 2008] action exited with status 0
[Sat Sep 27 21:05:13 2008] completed event "hotkey ATKD 00000050 00000000"

```

In "/etc/acpi/events" you can find all events recognized. You can create new event or correct existing one (see man acpid). First try to locate event e.g.:
```
fgrep "00000050" /etc/acpi/events/*
```. If the file is found,  open it and find out what script is called for me it was "/etc/acpi/mailbtn.sh". There you can see what is actually executed.

If there is no log record, probably you have to insmod some acpi module for HP...

---

