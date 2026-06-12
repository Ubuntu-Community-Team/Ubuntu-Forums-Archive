---
title: "Difference between &quot;do-release-upgrade&quot; and &quot;do-release-upgrade -d&quot;"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by tirengarfio on 2009-02-18
Hi,

anyone can explain me the difference?

Bye

---

### Post by snova on 2009-02-18
```

$ do-release-upgrade --help
Usage: do-release-upgrade [options]

Options:
  -h, --help            show this help message and exit
[B]  -d, --devel-release   Check if upgrading to the latest devel release is
                        possible[/B]
  -p, --proposed        Try upgrading to the latest release using the upgrader
                        from $distro-proposed
  -m MODE, --mode=MODE  Run in a special upgrade mode. Currently 'desktop' for
                        regular upgrades of a desktop system and 'server' for
                        server systems are supported.
  -f FRONTEND, --frontend=FRONTEND
                        Run the specified frontend

```

As explained by do-release-upgrade itself, it checks for development releases.

---

