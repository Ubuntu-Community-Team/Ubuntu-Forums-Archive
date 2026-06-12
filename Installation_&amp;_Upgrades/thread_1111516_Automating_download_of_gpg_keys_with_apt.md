---
title: "Automating download of gpg keys with apt?"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2009-03-30
I'm doing some major reinstallments in a bug-hunting effort thus my apt keys are wiped from time to time. This results in harmless, but annoying messages when i run apt-get in this style:
```

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E394067C90172836
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 04508D5C1654E635
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F5DCB1B62F1201A
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B8045AA69930E50

```


I know how to redeem the situation, but doing it manually for all GPG keys is quite tiresome. Therefore I wonder if anyone has a script to automate the process? Also, where are the GPG keys for apt stored so I back them up next time :)

Thanks!

---

### Post by sisco311 on 2009-03-30
[thread]1056099[/thread]

---

### Post by KhaaL on 2009-03-30
My thanks! :-)

---

