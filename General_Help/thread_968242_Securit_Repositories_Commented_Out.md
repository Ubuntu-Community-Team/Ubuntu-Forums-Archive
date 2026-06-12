---
title: "Securit Repositories Commented Out"
date: 2008-11-02
forum: General Help
---

### Post by brandoncolorado on 2008-11-02
I was looking through my sources.list file and found this section of code:

```

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe
```

When looking at the repositories listed in my synaptic package manager, I have the 'Important Security Updates' box checked.

Should I uncomment some of these?  Should I uncheck the repository listing and then uncomment them?

Thank you

---

### Post by plucky on 2008-11-02
> should I uncomment some of these? Should I uncheck the repository listing and then uncomment them?


**No** ```
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe
```

That line covers the all the other lines except the "deb-src" repository.

---

### Post by brandoncolorado on 2008-11-02
> **plucky said:**
> **No** ```
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe
```

That line covers the all the other lines except the "deb-src" repository.

Thanks.  Which of the deb-src lines should I un-comment?

---

### Post by plucky on 2008-11-02
> **brandoncolorado said:**
> Thanks.  Which of the deb-src lines should I un-comment?

Not necessary,unless you need the source code of the debs you download.

---

