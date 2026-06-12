---
title: "apparmor: genprof  error"
date: 2008-09-11
forum: General Help
---

### Post by tehhi on 2008-09-11
I want to test functionality of aa-genprof utility from apparmor-utils package. I enter such command:
```

sudo aa-genprof /usr/bin/firefox

```

And then I start firefox in other window and make random actions. After that I press 'S' in genprof and it start to scan /var/log/message. But it doesn't generate profile, because error happen:
```

Log contains unknown mode :w // or 1.5.2 or ssion

```

Why it's happen?

P.S. I use kubuntu under VirtualBox

---

