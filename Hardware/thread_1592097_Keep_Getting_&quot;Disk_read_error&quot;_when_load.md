---
title: "Keep Getting &quot;Disk read error&quot; when loading Windows XP"
date: 2010-10-10
forum: Hardware
---

### Post by Zavin on 2010-10-10
When I try to load Windows, I  get a message that says "A disk read error occurred. Press ctrl+alt+delete to restart."  Sometimes it'll just freeze on the GRUB screen when I select Windows.  It will load Ubuntu 9.10 without any problems, but I'm having major issues when I try to load Windows XP's partition.  I'm using a brand new hard drive that I bought 2 days ago.  Can anyone help me figure out what's going on and how to fix it? Thank you.

---

### Post by c0nv1ct on 2010-10-10
Have you checked the drive with smartctl (from smartmontools package) to verify the drive is in good health even if it is new?

```
sudo smartctl -t short /dev/sda
```

and/or

```
sudo smartctl -t long /dev/sda
```

and then this to view results

```
sudo smartctl --log=selftest /dev/sda
```

---

### Post by Zavin on 2010-10-10
Is that available in ubuntu, the bios, or online?

---

### Post by Zavin on 2010-10-10
I went to system-administration-disk@utility and in there it says SMART status: disk is healthy. Is that what u meant?

---

### Post by c0nv1ct on 2010-10-10
> **Zavin said:**
> I went to system-administration-disk@utility and in there it says SMART status: disk is healthy. Is that what u meant?

I mean exactly the commands I gave.  If you don't have smartmontools install it with:

```
sudo apt-get install smartmontools
```

Then run the commands I suggested to test the drive.

---

### Post by Zavin on 2010-10-10
I tried that but it keeps asking for a password. I typed the same one I use to log in but it says its incorrect. And I asked if its pre installed b/c I can't get online with it yet (I'm posting this from my cell). Oh well if nothing else ill just take it back tomorrow

---

