---
title: "Configuring a local mirror"
date: 2012-05-31
forum: Hardware
---

### Post by piriton on 2012-05-31
Hey

I know that software center / select sources can configure my local country's repository, but I wondered if there was a command line tool which also modified sources.list by finding the fastest local mirror.

Or a tool to configure sources.list and specify my country as France.

I can search and replace us for fr, but would like to know if there is a tool to do this.

---

### Post by piriton on 2012-06-01
Is there any problem in using this solution ?

```

perl -pi-OLD -e 's/\/\/us\./\/\/fr\./g' /etc/apt/sources.list

```

---

