---
title: "dpkg error"
date: 2008-10-24
forum: General Help
---

### Post by fadastic on 2008-10-24
Well, apparently I crashed while trying to install a LAMP server via tasksel (I ctrl+Z'd before it finished).

Running either "sudo apt-get -f install" or "sudo dpkg --configure -a" (as similar help threads suggest) gets me this:
```

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
```

And here's the error message I get when trying to install **any** package:
```

E: apache2.2-common: package apache2.2-common is not ready for configuration
```

---

### Post by geirha on 2008-10-25
After hitting ^Z, did you run bg to run it in the background, or did you just let it stay paused?

What happens if you try to remove apache2.2-common? ```
sudo aptitude remove apache2.2-common
```

---

