---
title: "NT1PlusII USB ISDN Modem Lockup"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by themacmeister on 2005-10-05
After using Ubuntu 5.0.4 Hoary Install, and mucking around with the BIOS because my favourite dd/ntldr method of dual-booting did not work, I discovered a problem that stopped me from using Ubuntu for more than 30min.

My NT1PlusII USB ISDN modem was originally detected and worked (same settings/init as FC3 which work perfectly). After disconnecting (wvdial or KPPP) the modem is frozen, and cannot be used again under Linux. Even under WinXP it still requires a hard reset to get working (unplugged for 10 secs from everything including power, and re-synced for 15sec).

This is a shame, since it looks like a wonderful distro. I believe it may be a broken cdc_acm module, which plagued users of kernel 2.6.9 as well. I tried a rebuild of 2.6.11.2 but the system was unbootable, due to no initrd support (vanilla source).

If anyone can give me a http/ftp/torrent link to the patched Hoary kernel-source, I would be very happy. (or even http/ftp access to a repository or two might help as well).

Cheers

---

