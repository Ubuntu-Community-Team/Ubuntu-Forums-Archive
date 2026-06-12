---
title: "Ubuntu update crashes new ATI driver"
date: 2009-02-17
forum: Hardware
---

### Post by oregonbob on 2009-02-17
I just did an update (been getting a LOT of those lately), then reboot my machine and it crashes when gnome starts with error messages:

Feb 17 00:13:32 tude kernel: [   35.099944] fglrx: Unknown symbol pci_unregi
ster_driver
Feb 17 00:13:32 tude kernel: [   35.099971] fglrx: disagrees about version o
f symbol vmalloc_to_page
Feb 17 00:13:32 tude kernel: [   35.099978] fglrx: Unknown symbol vmalloc_to
_page
Feb 17 00:13:32 tude kernel: [   35.099984] fglrx: disagrees about version o
f symbol wake_up_process
Feb 17 00:13:32 tude kernel: [   35.099987] fglrx: Unknown symbol wake_up_pr
ocess
Feb 17 00:13:32 tude kernel: [   35.100012] fglrx: disagrees about version o
f symbol find_vma
Feb 17 00:13:32 tude kernel: [   35.100020] fglrx: Unknown symbol find_vma
Feb 17 00:13:32 tude kernel: [   35.100112] fglrx: disagrees about version o
f symbol kill_fasync
Feb 17 00:13:32 tude kernel: [   35.100119] fglrx: Unknown symbol kill_fasyn

---

### Post by tenmoi on 2009-02-17
Did you install fglrx manually?
Try this: sudo aticonfig --initial -f
If this fails you, google for a howto install ATI.

---

