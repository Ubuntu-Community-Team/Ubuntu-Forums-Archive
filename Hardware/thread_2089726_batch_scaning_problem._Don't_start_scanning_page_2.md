---
title: "batch scaning problem. Don't start scanning page 2"
date: 2012-11-30
forum: Hardware
---

### Post by vlad2005 on 2012-11-30
Hi!
I have xubuntu 12.04 with all updates.
Also i have an HP Deskjet 1050A. Everything work well, but for speed i want to scan documents from command line.
For single document work well using scanimage. But i want to use batch scaning, so i do'it with this command:
```

scanimage --resolution 200 --batch --batch-start 1 --batch-count 5 >out.pnm

```
After first page is scanned, cannot continue scanning next page.
Message in console is below:
```

Scanning 5 pages, incrementing by 1, numbering from 1
Scanning page 1
Scanned page 1. (scanner status = 5)
Scanning page 2 
(here stopped)

```
On my system i have hplip 3.12.2-1ubuntu3.1

Any suggestion?

---

