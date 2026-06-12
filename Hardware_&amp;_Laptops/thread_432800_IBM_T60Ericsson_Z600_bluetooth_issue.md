---
title: "IBM T60/Ericsson Z600 bluetooth issue"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by killerdrone on 2007-05-04
Hi, 
i'm trying to connect to my mobile phone (Ericsson Z600) via bluetooth, and i think i'm really close to get it to work. I can see the phone with "hcitool scan" and in multisync. When i click "test connection" in multisync i get a dialog on the phone asking me if i want to add the computer as a device. When i answer "yes", it asks for a passphrase. I enter the one specified in hcid.conf (is this correct?), and get the message "bluetooth connection failed" on the phone, and something similiar in multisync. After some experimenting i noticed that my dmesg was filled with this junk: 

```
[ 9736.104000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 12
[ 9736.124000] l2cap_recv_acldata: Unexpected continuation frame (len 0)

```

Could this be a bug? Seems it has worked for other people under similiar conditions. One thing, i haven't found anything on the phone about setting a password for bluetooth access, as in hcid.conf on the computer. Could it be that simple?

---

