---
title: "Help - Nokia D-211 WLAN/GPRS/GSM Card"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by yuyang99 on 2005-08-20
Hello All,

I just installed Ubuntu on my IBM T20 and it works perfect. Now I want to config my Nokia D-211 WLAN/GPRS/GSM card with Ubuntu but I am just a beginning - not idea how to do it. Any one can help me?

Here is some backgrounds

There is one Nokia release beta driver for this D-211 card, and driver is in source code. So the first thing I need is to compile it to a driver for Ubuntu - how can I do it? Here is the "configuration" file I need to do, any one can give me a help?

---

# User Settings EDIT THESE TO MATCH YOUR CONFIGURATION!
# LINUX = /usr/src/linux               # Linux is here
# OS_RELEASE=2.4.12                    # Kernel version for module inst.
# INSTDIR=/sbin                        # Install tools here
# ROOTDIR=/                            # Root for kernel module installation
# SMAC2=d211fw.bin		       # Firmware for the card

LINUX = /usr/src/linux
OS_RELEASE=2.4.12
ROOTDIR=/
SMAC2=d211fw.bin

# Compiler Settings

CROSS_COMPILE=

LD	= $(CROSS_COMPILE)ld
CC	= $(CROSS_COMPILE)gcc
CPP	= $(CROSS_COMPILE)g++
AR	= $(CROSS_COMPILE)ar
RANLIB	= $(CROSS_COMPILE)ranlib

-------------------------------------------------

---

