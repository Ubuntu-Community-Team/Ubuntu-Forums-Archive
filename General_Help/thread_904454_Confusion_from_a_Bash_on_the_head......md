---
title: "Confusion from a Bash on the head....."
date: 2008-08-29
forum: General Help
---

### Post by laurence91 on 2008-08-29
Hello, im trying to install a program for work and i cant get passed one section todo with environment variables.

setenv CCPNMR_TOP_DIR directory_where_you_unpacked_release/ccpnmr

Above is the code i need to use but i know 'setenv' is not a stand alone command in Bash, so really what i would like to know is what would be the equivelent in Kubuntu 8.04?

I know it starts with 'export = ' but im not having much luck

Thanks in advance

Laurence

---

### Post by maybeway36 on 2008-08-29
> **laurence91 said:**
> Hello, im trying to install a program for work and i cant get passed one section todo with environment variables.

setenv CCPNMR_TOP_DIR directory_where_you_unpacked_release/ccpnmr

Above is the code i need to use but i know 'setenv' is not a stand alone command in Bash, so really what i would like to know is what would be the equivelent in Kubuntu 8.04?

I know it starts with 'export = ' but im not having much luck

Thanks in advance

Laurence

Try this:
```
export CCPNMR_TOP_DIR=directory_where_you_unpacked_release/ccpnmr
```

---

