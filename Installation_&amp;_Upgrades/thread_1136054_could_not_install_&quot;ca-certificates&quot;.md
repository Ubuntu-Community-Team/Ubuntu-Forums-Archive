---
title: "could not install &quot;ca-certificates&quot;"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by bkbk on 2009-04-24
I just used the Update Manager to upgrade to 9.04. Everything seemed to go OK, except it said it could not install ca-certificates. The explanation was:
subprocess post-installation script returned error exit status 1

There were a bunch of dire warnings about the upgrade failing, etc. (Also, I clicked to report the problem. Apport opened but then reporting the problem failed.) Anyway, I restarted the computer and everything I've looked at seems to be OK.

Does anyone know what ca-certificates does and how I can install it now? Thanks.

---

### Post by bkbk on 2009-04-25
I used the Synaptic Package Manager to search for "ca-certificates" and found that it is installed. I assume, then, that the error message I got during the upgrade was incorrect. At least, I hope so.

---

### Post by oygle on 2009-06-16
During the Jaunty upgrade, I got this message

> 
Could not install 'ca-certificates'

The upgrade will continue but the 'ca-certificates' package may be in a not working state. Please consider submitting a bug report about it.

subprocess post-installation script returned error exit status 1


but also found in Synaptic, that it is installed ??

---

