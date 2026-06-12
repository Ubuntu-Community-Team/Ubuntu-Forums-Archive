---
title: "Kooka crashes"
date: 2008-07-26
forum: General Help
---

### Post by ruipedroca on 2008-07-26
Hi,

Kooka has always worked well, but a few days ago it started crashing.
I really need the scanner utility for work purposes.
Can anyone help?

Regards

Here's the backtrace:
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb65556c0 (LWP 6450)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb602cbf5 in ?? () from /usr/lib/libmfp.so
#7  0xb602e842 in m_parport_ECP_supported () from /usr/lib/libmfp.so
#8  0xb602ecfd in port_init () from /usr/lib/libmfp.so
#9  0xb602ee8f in dpa_init () from /usr/lib/libmfp.so
#10 0xb602858f in mfp_get_devices () from /usr/lib/libmfp.so
#11 0xb60644ea in port::init_mfp_port_control ()
   from /usr/lib/sane/libsane-smfp.so.1
#12 0xb6054039 in device::init_mfp_port_control ()
   from /usr/lib/sane/libsane-smfp.so.1
#13 0xb60562f9 in driver::init_mfp_port_control ()
   from /usr/lib/sane/libsane-smfp.so.1
#14 0xb6051e06 in backend::init () from /usr/lib/sane/libsane-smfp.so.1
#15 0xb605181a in sane_smfp_init () from /usr/lib/sane/libsane-smfp.so.1
#16 0xb68d693d in ?? () from /usr/lib/libsane.so.1
#17 0xb68d6c5d in sane_dll_get_devices () from /usr/lib/libsane.so.1
#18 0xb68d71c4 in sane_get_devices () from /usr/lib/libsane.so.1
#19 0xb7a25bf6 in KScanDevice::KScanDevice () from /usr/lib/libkscan.so.1
#20 0x0807ebed in ?? ()
#21 0x0807f465 in ?? ()
#22 0x0808d567 in ?? ()
#23 0xb779c450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#24 0x08064bb1 in ?? ()

---

### Post by ProbablyX on 2008-07-26
Did you install, remove or upgrade any software - in particular KDE system files - arround the time this started happening?

---

### Post by ruipedroca on 2008-07-26
Yes, I did, several. 
What should I do, now?..

---

### Post by ruipedroca on 2008-07-29
Solved this by making a fresh install of the OS!

---

