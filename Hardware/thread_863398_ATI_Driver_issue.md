---
title: "ATI Driver issue"
date: 2008-07-18
forum: Hardware
---

### Post by Unotforme on 2008-07-18
Hi. I'm new to Linux (recently installed HH 8.04 as a standalone OS). I recently downloaded (upgraded) a proprietary driver for my ATI video card through ADMIN>HARDWARE DRIVERS. The problem I'm now having is that my synaptic manager now won't run due to several erros (as well as Applications>Add/Remove), so I don't know how else to remove the newer driver (or at least revert back to the original Ubuntu driver). I believe that installing the new driver caused my synaptic manager error, as everything was working up until I installed it. 

I can get into terminal, but I've no idea what commands to use there. I can't post the errors at the moment, as I'm not currently at home, but any suggestions to try when I do, would be greatly appreciated.

---

### Post by overdrank on 2008-07-18
> **Unotforme said:**
> Hi. I'm new to Linux (recently installed HH 8.04 as a standalone OS). I recently downloaded (upgraded) a proprietary driver for my ATI video card through ADMIN>HARDWARE DRIVERS. The problem I'm now having is that my synaptic manager now won't run due to several erros (as well as Applications>Add/Remove), so I don't know how else to remove the newer driver (or at least revert back to the original Ubuntu driver). I believe that installing the new driver caused my synaptic manager error, as everything was working up until I installed it. 

I can get into terminal, but I've no idea what commands to use there. I can't post the errors at the moment, as I'm not currently at home, but any suggestions to try when I do, would be greatly appreciated.

Hi and could you post the output of the commands ```
 sudo apt-get update
sudo apt-get upgrade
```
Please use the code tags in your reply to conserve space and easy reading.
```
Like this 
```

---

### Post by Unotforme on 2008-07-18
I have ran those commands, and received the same error messages that synaptic gives me when I load up. I can't post those erros though until I get home.

---

### Post by overdrank on 2008-07-18
> **Unotforme said:**
> I have ran those commands, and received the same error messages that synaptic gives me when I load up. I can't post those erros though until I get home.

ok do you remember the error message?

---

### Post by Unotforme on 2008-07-18
I get this message in terminal and in synaptic:

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing scim-gtk2-immodule (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

