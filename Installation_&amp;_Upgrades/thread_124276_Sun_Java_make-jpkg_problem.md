---
title: "Sun Java: make-jpkg problem"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by Lykurg on 2006-02-01
Hi,

I am going to install Sun's Java JDK, and folowed the instructions from [http://wiki.ubuntu.com/RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats"). But I get folowing error:
```
hiwi@wagd28:~$ fakeroot make-jpkg jdk-1_5_0_06-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXK19dOk
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

```

So I try ```
DEB_BUILD_GNU_TYPE=amd64-generic fakeroot make-jpkg jdk-1_5_0_06-linux-i586.bin
```
which returns the same error.

Do I need any other packages than fakeroot, java-package and java-common?

Thanks,
Lykurg

EDIT: I found the bottom! (Java on amd64 computers)

---

