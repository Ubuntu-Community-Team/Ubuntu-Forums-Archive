---
title: "Cannot get php4 installed on 5.10"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by cj5 on 2006-01-26
When I run 'sudo apt-get install php4' I get this output:

```
Reading package lists... Done
Building dependency tree... Done
Package php4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package php4 has no installation candidate
```

I updated my sources.list file, and I still am having this issue. Any ideas?

Cheers,
CJ...:confused:

---

### Post by Koobi on 2006-01-26
weird...try:
```

apt-cache search php4

```


does "php4" appear on that list?

---

