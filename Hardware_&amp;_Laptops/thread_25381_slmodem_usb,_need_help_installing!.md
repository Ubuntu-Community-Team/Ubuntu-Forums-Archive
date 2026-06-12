---
title: "slmodem usb, need help installing!"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by mortram on 2005-04-10
{reposting because i think it posted in the wrong forum originally}

56k Best Data USB Modem

I bought this modem because it specifically said it was linux compatible, however I've had no luck installing it with their pre-made rpms on Fedora or with the source in Ubuntu (4.10 & 5.0.4). Having only dial-up access, configuring this modem is the only thing keeping me from switching from Windows!

I've made it as far as copying the driver source files to my a folder in my home directory and installing gcc through Synaptic in order to compile, but it ends with erros. I will post the Makefile and perhaps someone can solve the mystery for me...

the command I attempted to run was 'make install-usb'

thanks for helping me get around this, Ubuntu seems like a great distro and I'd love it to be my everyday OS.

################################################## #########################
#
#
# Makefile -- Smart Link Soft Modem product Makefile.
#
# Copyright (C) 2001
# Smart Link Ltd. ([www.smlink.com](www.smlink.com))
#
# Author: Sasha K (sashak@smlink.com)
#
#
####################

############################## #########################
#
################################################## #########################


# Tools
CC := gcc
LD := ld
INSTALL := install
DEPMOD := /sbin/depmod
MODPROBE:= /sbin/modprobe
RM := rm
LN := ln
SED := sed
GREP := grep
CP := cp
MKNOD := mknod

# debug mode options /* off */
# DEBUG:=0
-include debug.mk

# Definitions
MODULES_DIR = /lib/modules/$(shell ./kernel-ver)/misc
MODEM_DEV := ttySL0
MODEM_LINK := modem
MODULES_CONF:= /etc/modules.conf

# Path to your kernel's includes
ifndef KERNEL_INCLUDES
KERNEL_INCLUDES:= /usr/src/linux/include
endif

INCLUDES := -I. -I$(KERNEL_INCLUDES)

ifndef MODVERSIONS_FLAGS
MODVERSIONS_FLAGS= -DMODVERSIONS --include $(KERNEL_INCLUDES)/linux/modversions.h
endif


# C FLAGS
CFLAGS:= -Wall -O3 -fomit-frame-pointer -D__KERNEL__ -DMODULE -DEXPORT_SYMTAB $(INCLUDES) $(MODVERSIONS_FLAGS)
#CFLAGS:= -Wall -O3 -fomit-frame-pointer -DMODEM_DEBUG=$(DEBUG) -D__KERNEL__ -DMODULE -DEXPORT_SYMTAB $(INCLUDES) $(MODVERSIONS_FLAGS)
ifdef DEBUG
CFLAGS += -DMODEM_DEBUG=$(DEBUG)
endif
LFLAGS=

SLMDM := slmdm.o
SLAMR := slamrmo.o
SLUSB := slusb.o
SLFAX := slfax.o

ALL_MODULES := $(SLAMR) $(SLUSB) $(SLMDM) $(SLFAX)
ALL_TARGETS := $(ALL_MODULES)

SLAMR_OBJ := amrmo.o
SLUSB_OBJ := usb.o
SLMDM_OBJ := mdm.o
SLFAX_OBJ := fax.o

MDM_OBJS := mdm_init.o mdm_sltty.o mdm_params.o
FAX_OBJS := fax_init.o
AMR_OBJS := amrmo_init.o
USB_OBJS := usb_st7554.o
CUSTOM_OBJ := editme.o
SYSDEP_OBJ := sysdep.o
SYSDEP_LINUX_OBJ:= sysdep_linux.o
SYSDEP_PCI_OBJ := sysdep_pci.o


all: $(ALL_TARGETS) kernel-ver

$(SLAMR): $(SLAMR_OBJ) $(AMR_OBJS) $(SYSDEP_PCI_OBJ)
$(SLUSB): $(SLUSB_OBJ) $(USB_OBJS)
$(SLMDM): $(SLMDM_OBJ) $(MDM_OBJS) $(CUSTOM_OBJ) $(SYSDEP_OBJ) $(SYSDEP_LINUX_OBJ)
$(SLFAX): $(SLFAX_OBJ) $(FAX_OBJS)

$(ALL_MODULES):
$(LD) -r -o $@ $^

kernel-ver: kernel-ver.o

install-amr: install config-amr
install-usb: install config-usb

install: kernel-ver all
$(INSTALL) -D -m 644 slmdm.o $(prefix_dir)/$(MODULES_DIR)/slmdm.o
$(INSTALL) -D -m 644 slfax.o $(prefix_dir)/$(MODULES_DIR)/slfax.o
$(INSTALL) -D -m 644 slamrmo.o $(prefix_dir)/$(MODULES_DIR)/slamrmo.o
$(INSTALL) -D -m 644 slusb.o $(prefix_dir)/$(MODULES_DIR)/slusb.o
$(INSTALL) -D -m 755 country.dat $(prefix_dir)/etc/country.dat
$(INSTALL) -d $(prefix_dir)/dev
$(RM) -f $(prefix_dir)/dev/$(MODEM_DEV)
$(MKNOD) -m 666 $(prefix_dir)/dev/$(MODEM_DEV) c 212 0
$(LN) -sf ./$(MODEM_DEV) $(prefix_dir)/dev/$(MODEM_LINK)

uninstall: kernel-ver cleanup-config unload-modules
$(RM) -f $(prefix_dir)/$(MODULES_DIR)/slmdm.o
$(RM) -f $(prefix_dir)/$(MODULES_DIR)/slfax.o
$(RM) -f $(prefix_dir)/$(MODULES_DIR)/slamrmo.o
$(RM) -f $(prefix_dir)/$(MODULES_DIR)/slusb.o
$(RM) -f $(prefix_dir)/etc/country.dat
$(RM) -f $(prefix_dir)/var/lib/slmdm.data
$(RM) -f $(prefix_dir)/dev/$(MODEM_DEV)
$(RM) -f $(prefix_dir)/dev/$(MODEM_LINK)

config-usb: config
$(CP) $(MODULES_CONF) $(MODULES_CONF).slmdm && \
$(SED) -e 's/^alias slmodem .*$$/alias slmodem slusb/' $(MODULES_CONF).slmdm > $(MODULES_CONF)
-$(DEPMOD) -a

config-amr: config
$(CP) $(MODULES_CONF) $(MODULES_CONF)\.slmdm && \
$(SED) -e 's/^alias slmodem .*$$/alias slmodem slamrmo/' $(MODULES_CONF).slmdm > $(MODULES_CONF)
-$(DEPMOD) -a

config: cleanup-config
-$(CP) $(MODULES_CONF) $(MODULES_CONF).slmdm
echo 'alias char-major-212 slmodem' >> $(MODULES_CONF)
echo 'alias slmodem off' >> $(MODULES_CONF)

cleanup-config: unload-modules
-$(CP) $(MODULES_CONF) $(MODULES_CONF).slmdm && \
$(GREP) -v 'slmodem' $(MODULES_CONF).slmdm > $(MODULES_CONF)
-$(DEPMOD) -a

unload-modules:
-$(MODPROBE) -r slusb
-$(MODPROBE) -r slamrmo
-$(MODPROBE) -r slfax
-$(MODPROBE) -r slmdm

spec-file-lists: slmdm.modules slamr.modules slusb.modules

%.modules: kernel-ver
@echo "build modules list spec file $@..."
$(SED) -e 's/%modules_dir/$(subst /,\/,$(MODULES_DIR))/' $@-dist > $@

clean:
$(RM) -f $(ALL_TARGETS) $(MDM_OBJS) $(FAX_OBJS) $(AMR_OBJS) $(USB_OBJS) $(CUSTOM_OBJ) $(SYSDEP_OBJ) $(SYSDEP_LINUX_OBJ) $(SYSDEP_PCI_OBJ) kernel-ver kernel-ver.o
$(RM) -f *.modules

%.o: %.c
$(CC) $(CFLAGS) -o $@ -c $<

dep:
$(CC) -M -c $(CFLAGS) *.c > .depend
-include .depend

---

### Post by az on 2005-04-10
sudo apt-get install build-essential linux-headers-2.6.10-5-386

but first try:
[http://apqi.com/ubuntu/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-29_i386.deb](http://apqi.com/ubuntu/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-29_i386.deb)
[http://apqi.com/ubuntu/sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb](http://apqi.com/ubuntu/sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb)

---

### Post by mortram on 2005-04-10
okay, tried to install the packages, but was unsuccessful.  these were the results, there may be something in here that tells me exactly what's wrong but the output is a bit cryptic to me:

troy@ubuntu:/mnt/localdiskD$ sudo dpkg -i sl-modem-daemon_2.9.9a-1ubuntu2_i386.d eb
Password:
Selecting previously deselected package sl-modem-daemon.
(Reading database ... 29397 files and directories currently installed.)
Unpacking sl-modem-daemon (from sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb) ...
dpkg: dependency problems prevent configuration of sl-modem-daemon:
 sl-modem-daemon depends on sl-modem-modules-new | sl-modem-source (>> 2.9.6-1);  however:
  Package sl-modem-modules-new is not installed.
  Package sl-modem-source is not installed.
dpkg: error processing sl-modem-daemon (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sl-modem-daemon


troy@ubuntu:/mnt/localdiskD$ sudo dpkg -i sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-29_i386.deb
Selecting previously deselected package sl-modem-modules-2.6.10-5-386.
(Reading database ... 29408 files and directories currently installed.)
Unpacking sl-modem-modules-2.6.10-5-386 (from sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-29_i386.deb) ...
Setting up sl-modem-modules-2.6.10-5-386 (2.9.9a-1ubuntu2+2.6.10-29) ...
/var/lib/dpkg/info/sl-modem-modules-2.6.10-5-386.postinst: line 27: /etc/init.d/sl-modem-daemon: No such file or directory



so, I tried to compile it again after installing the linux headers, resulting in:

troy@ubuntu:~/slmdm-2.7.14$ make install-usb
gcc -Wall -O3 -fomit-frame-pointer -D__KERNEL__ -DMODULE -DEXPORT_SYMTAB -I. -I/usr/src/linux/include  -DMODVERSIONS --include /usr/src/linux/include/linux/modversions.h -o kernel-ver.o -c kernel-ver.c
<command line>:138477883:384: /usr/src/linux/include/linux/modversions.h: No such file or directory
make: *** [kernel-ver.o] Error 1
troy@ubuntu:~/slmdm-2.7.14$


where to go from here?

---

### Post by mortram on 2005-04-10
well, it seems that in order to get those packages to install, I just had to reverse the commands and install the 'modules' package first.  so the modem appears to have installed successfully.  However, something is still not right, the 'sldaemon' does not appear to be loaded or to load during startup, and I can't activate 'ppp0' from with the the Gnome Network configuration panel.  the link it creates at /dev/modem to ttySL0 does not appear to be valid.  This was the message after it installed:

root@ubuntu:/mnt/localdiskD/Downloads/system/Linux # dpkg -i sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb
(Reading database ... 29415 files and directories currently installed.)
Preparing to replace sl-modem-daemon 2.9.9a-1ubuntu2 (using sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb) ...
Shutting down SmartLink Modem driver normally ...[COLOR=Red] no slmodemd daemon running.[/COLOR]
Unpacking replacement sl-modem-daemon ...
Setting up sl-modem-daemon (2.9.9a-1ubuntu2) ...
Loading ALSA modem driver into kernel ... done.
Starting SmartLink Modem driver for: .
Creating /dev/modem symlink, pointing to: /dev/ttySL0.


when exiting it also gives the 'no slmodemd daemon running'.  Is there another step that I need to take beyond installing the packages?

---

