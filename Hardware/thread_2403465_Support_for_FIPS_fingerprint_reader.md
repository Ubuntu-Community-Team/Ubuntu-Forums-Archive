---
title: "Support for FIPS fingerprint reader"
date: 2018-10-11
forum: Hardware
---

### Post by hsz# on 2018-10-11
I have installed today latest Ubuntu 18.04 on Dell Precision 3530 and everything went very smoothly except fingerprint support.
As far as I know this fingerprint reader is called FIPS, but I couldn't find any details about that:

[IMG]https://img.purch.com/o/aHR0cDovL2Nkbi5sYXB0b3BtYWcuY29tL2ltYWdlcy91cGxvYWRzL3BwcmVzcy80NTY3OC9kZWxsLXByZWNpc2lvbi0zNTMwLTAxMi5qcGc=[/IMG]

I have tried every method of installing the fp drivers and tools but even `lsusb` doesn't print fingerprint related entries.

What can I do about that?

---

### Post by TheFu on 2018-10-12
FIPS is a US govt standard [https://en.wikipedia.org/wiki/Federal_Information_Processing_Standards](https://en.wikipedia.org/wiki/Federal_Information_Processing_Standards)  Use lsusb or lspci to find more data about the specific reader.

If you are trying to be secure from a relative, these are fine.

---

