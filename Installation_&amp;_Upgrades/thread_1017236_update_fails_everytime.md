---
title: "update fails everytime"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by dd000d on 2008-12-20
ubuntu 8.04 hardy heron won't update anymore. Everytime i try to update it it comes up with this message...

    ```
Reading package lists... Error!

    E: Problem parsing dependency Recommends

    E: Error occurred while processing thunderbird (NewVersion1)

    E: Problem with MergeList /var/lib/dpkg/status

    E: The package lists or status file could not be parsed or opened.
```

i tried removing thunderbird and i get this message as well

   ```
 Reading package lists... Error!

    E: Problem parsing dependency Recommends

    E: Error occurred while processing thunderbird (NewVersion1)

    E: Problem with MergeList /var/lib/dpkg/status

    E: The package lists or status file could not be parsed or opened.


```

---

### Post by taurus on 2008-12-20
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

