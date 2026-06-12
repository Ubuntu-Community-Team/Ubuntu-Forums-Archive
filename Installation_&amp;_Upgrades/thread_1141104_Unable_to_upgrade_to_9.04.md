---
title: "Unable to upgrade to 9.04"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by svsig on 2009-04-28
I am trying to upgrade from 8.10 to 9.04, but I get some error messages and the upgrade is aborted.

Here is the message I get:

[SIZE="3"]**Could not download the upgrades**[/SIZE]

The upgrade is now aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.

```
Failed to fetch http://no.archive.ubuntu.com/ubuntu/pool/universe/c/checkbox/hwtest_0.7.1_all.deb 403 Forbidden
Failed to fetch http://no.archive.ubuntu.com/ubuntu/pool/universe/libc/libcaca/libcucul0_0.99.beta16-1_all.deb 403 Forbidden
Failed to fetch http://no.archive.ubuntu.com/ubuntu/pool/universe/a/acpi/acpi_1.2-1ubuntu1_i386.deb 403 Forbidden
Failed to fetch http://no.archive.ubuntu.com/ubuntu/pool/universe/a/app-install-data-partner/app-install-data-commercial_11.9.04_all.deb 403 Forbidden
Failed to fetch http://no.archive.ubuntu.com/ubuntu/pool/universe/b/bug-buddy/bug-buddy_2.26.0+dfsg-0ubuntu1_i386.deb 403 Forbidden
Failed to fetch http://no.archive.ubuntu.com/ubuntu/pool/universe/libc/libcommons-digester-java/libcommons-digester-java_1.8-2ubuntu1_all.deb 403 Forbidden
Failed to fetch http://no.archive.ubuntu.com/ubuntu/pool/universe/libg/libgda3/libgda3-sqlite_3.0.2-5ubuntu1_i386.deb 403 Forbidden
```

When I check the first url in the list I can't find the package hwtest_0.7.1_all.deb. However, I find 2 other packages here, hwtest-cli_0.7.1_all.deb and hwtest-gtk_0.7.1_all.deb.

Can somebody please help?

---

### Post by svsig on 2009-04-28
The problem is solved. Suddenly the packages were available again. I don't know what has happened, but at least I could finish my upgrade.

---

