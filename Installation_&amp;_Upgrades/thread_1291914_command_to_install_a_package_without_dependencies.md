---
title: "command to install a package without dependencies?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by vksingh on 2009-10-15
Hi,

What is the command to install a .deb package without dependencies?

Thanks,

Vivek:(

---

### Post by mcduck on 2009-10-15
Why would you do that? You'd only end with a broken install and non-functional program.

The package you are trying to install depends on other packages to provide some functionalities, so installing it without installing those dependencies would only result in broken program.

(the "-f" switch for dpkg will force install, but like I said doing that will most likely just break things)

---

### Post by Mark Phelps on 2009-10-17
The command is dpkg -- but it won't work because unless you are able to satisfy the dependencies, it won't complete the install.

---

