---
title: "UEFI + MSI A75MA-G55 + Ubuntu issues"
date: 2011-10-26
forum: Hardware
---

### Post by bobthemaniac on 2011-10-26
This motherboard filter's the boot entry list and will only display
boot entry's with the label of "Windows Boot Manager" so once the
install of Ubuntu completes you will not be able to boot.

to work around this limitation you will need to install the Ubuntu 
boot entry with the label of "Windows Boot Manager"

```

sudo efibootmgr -v -c -L "Windows Boot Manager" -l "\\EFI\\ubuntu\\grubx64.efi"

```

see this thread for more info

[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

