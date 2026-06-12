---
title: "855gm graphics card page flip errors"
date: 2011-03-02
forum: Hardware
---

### Post by cooper_d on 2011-03-02
I have installed a patched kernel for Ubuntu 10.10 but am still getting issues with page flipping for my 855gm graphics card.

Videos play fine now but if I use a screensaver with rotating shapes, for example, they preview perfectly in the full screen view. However, when the screensaver starts naturally after the preset time, 'syslog' and 'kern.log' literally fill my disk up with the following errors:

[I]Mar 2 09:28:48 dave-laptop kernel: [ 268.018755] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018773] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018791] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018808] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018826] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018844] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018862] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018879] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018897] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018915] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018933] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018951] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018969] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.018986] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.019004] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.019022] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.019040] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.019058] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar 2 09:28:48 dave-laptop kernel: [ 268.019075] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
[/I]
Does anyone know how to fix this? I have tried disabling graphic acceleration but then the screensavers are all jerky and presumably games won't run smoothly either and videos will also suffer, but I certainly don't get the error messages if I do that.

Any suggestions would be welcome.

---

### Post by sumski on 2011-06-08
[https://bugs.freedesktop.org/show_bug.cgi?id=30654#c10](https://bugs.freedesktop.org/show_bug.cgi?id=30654#c10)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765813](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765813)

---

