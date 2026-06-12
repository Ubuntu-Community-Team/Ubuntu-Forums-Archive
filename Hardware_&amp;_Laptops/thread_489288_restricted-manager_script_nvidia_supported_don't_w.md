---
title: "restricted-manager script nvidia_supported don't work with 100.14.11"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by Amnon82 on 2007-07-01
Hi there.

I'm one of the developers of Paldo GNU/Linux Distribution.
We have added restricted drivers as default and using nvidia_supported-script (from [restricted-manager](http://packages.ubuntu.com/feisty/admin/restricted-manager)) for making our modprobe-files for the restricted nvidia drivers (glx and legacy).

This is the script:

[http://pastebin.ca/585480](http://pastebin.ca/585480)

Today I get troubles. The output was this:

[http://pastebin.ca/585533](http://pastebin.ca/585533)

One of my older output with older drivers gave me this:

[http://pastebin.ca/585535](http://pastebin.ca/585535)

So it has something to do with nvidia.ko the new 100.14.11 driver. 100.14.09 didn't had this problems at all. So what can I do? Will the script be modified for the new driver releases?

---

### Post by jki on 2007-09-19
[http://heh.fi/tmp/nvidia_supported.diff](http://heh.fi/tmp/nvidia_supported.diff)

---

