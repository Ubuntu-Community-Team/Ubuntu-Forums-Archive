---
title: "Oracle forms application does not work, must be Ubuntu kernel issue"
date: 2008-09-22
forum: General Help
---

### Post by georgz on 2008-09-22
Hiya,

for work I have to use an Oracle forms based application which is delivered via browser as a java applet.

For this, I have created a separate user "appl" and have downloaded firefox and jre1.6 and installed in the users home directory. This is so that this application does not disturb my work in the main firefox browser.

This worked fine up to 7.10.

Now with 8.04.1 I startthe same browser/jdk version from the user "appl"s homedir, and the application starts up, but within the application no database rows are displayed (it's a viewer for database records, so each row for one record).

It cannot be related to the firefox/jdk version, the same binaries work on 7.10.

Any tips for further debugging? I have no idea anymore. This must be in the xserver or libc, kernel area...

What I have tested so far:

* Works fine in 7.10 (both with default Firefox or self installed Firefox
* Does not work in 8.04.1 and Intrepid
* Does not work on amd64 versions because the app does not work with the open source java

On 8.04.1 and Intrepid I tested all possible scenarios:
- tested with/out Desktop Effects
- tested with/out fglrx and ati driver
- tested via remote connection/xdisplay redirect
and and and.

The only way that I got it to work was to copy over the old kernel with it's modules from 7.10 to 8.04.1. With this kernel booted, it works fine.

Strange, isn't it?

What I'm searching for is advice to further debugging... Any help?

TIA

---

### Post by georgz on 2008-09-26
Just4info, this seems to be a generic issue, it happens to all kernels 2.6.24 and above, even the stock kernels from kernel.org. I also verified it on openSuse. Not Ubuntu specific. Although I would really like to know what the change was in 2.6.24...

---

