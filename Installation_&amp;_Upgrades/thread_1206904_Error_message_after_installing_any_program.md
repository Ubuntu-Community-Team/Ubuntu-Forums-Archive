---
title: "Error message after installing any program"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by zepita on 2009-07-07
Hi,

I'm getting the following error everytime I install a new program or update the system.

```
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 pips-snx100
E: Sub-process /usr/bin/dpkg returned an error code (1)
mleyes@mleyes:~$ 

```


I know what pips-snx100 is. It's a driver for my printer that did not work and I uninstalled from the scrip that it came with the package.

Any suggestions?

Thanks

---

### Post by Brandon Williams on 2009-07-07
There should have been some additional output related to pips-snx100 that indicated something about the nature of the problem. Most likely, there is a problem with the postrm script (/var/lib/dpkg/info/pips-snz100.postrm), although a problem with the prerm script is also a possibility.

Although it's only to be used as a last resort, you could delete the offending script to clear up the problem. Something like this would do it:

```
sudo find /var/lib/dpkg/info/ -name 'pips-snx100.*' -executable -exec rm -f {} \;
```

After that, run 'sudo aptitude purge pips-snx100' to make sure that everything is cleaned up as well as possible.

The reason this approach is to be used only as a last resort is that the script may have some important cleanup tasks to do that will not be done if you simply delete it. It's a better idea to fix the script if you can.

---

### Post by zepita on 2009-07-07
> **Brandon Williams said:**
> There should have been some additional output related to pips-snx100 that indicated something about the nature of the problem. Most likely, there is a problem with the postrm script (/var/lib/dpkg/info/pips-snz100.postrm), although a problem with the prerm script is also a possibility.

Although it's only to be used as a last resort, you could delete the offending script to clear up the problem. Something like this would do it:

```
sudo find /var/lib/dpkg/info/ -name 'pips-snx100.*' -executable -exec rm -f {} \;
```

After that, run 'sudo aptitude purge pips-snx100' to make sure that everything is cleaned up as well as possible.

The reason this approach is to be used only as a last resort is that the script may have some important cleanup tasks to do that will not be done if you simply delete it. It's a better idea to fix the script if you can.

It worked pretty well. Thank you very much :)

---

