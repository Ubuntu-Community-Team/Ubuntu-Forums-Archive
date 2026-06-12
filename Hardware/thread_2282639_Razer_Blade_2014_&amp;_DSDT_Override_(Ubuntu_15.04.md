---
title: "Razer Blade 2014 &amp; DSDT Override (Ubuntu 15.04)"
date: 2015-06-15
forum: Hardware
---

### Post by Slither2007 on 2015-06-15
Hi,

 I need help identifying why my patched dsdt.aml file is not getting loaded by grub please. 

I've recently installed Ubuntu 15.04 with kernel 4.0.5 fresh as a dual boot OS alongside the factory installed Windows 8.1. (Guide [here]("http://supaevensteven.blogspot.com.au/2015/06/ubuntu-1504-razer-blade-14-2014.html")) I've followed the usual advice to load a dsdt.aml table file through the grub boot loader but after booting the dsdt tables loaded in /sys/firmware/acpi/tables/DSDT doesn't contain my changes. Looking through dmesg doesn't indicate the dsdt was loaded and no error to indicated why it wasn't.

My dsdt file is re-compiled with no errors or warnings. 

Here are the instructions I followed to get to this point : 

Dumped and extracted my dsdt tables:

```
sudo acpidump -o acpidump.txt
acpixtract acpidump.txt
iasl -da -dl *.dat
```

Patched DSDT with my changes

```
iasl -tc dsdt.dsl
```

Copied my re-compiled dsdt.aml file as /boot/dsdt.aml:

```
sudo cp dsdt.aml /boot/dsdt.aml
```

Copied the following and created this file here /etc/grub.d/01_acpi and made it executable:

```
#! /bin/sh -e

# Uncomment to load custom ACPI table
GRUB_CUSTOM_ACPI="/boot/dsdt.aml"

# DON'T MODIFY ANYTHING BELOW THIS LINE!

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

. ${libdir}/grub/grub-mkconfig_lib

# Load custom ACPI table
if [ x${GRUB_CUSTOM_ACPI} != x ] && [ -f ${GRUB_CUSTOM_ACPI} ] \
        && is_path_readable_by_grub ${GRUB_CUSTOM_ACPI}; then
    echo "Found custom ACPI table: ${GRUB_CUSTOM_ACPI}" >&2
    prepare_grub_to_access_device `${grub_probe} --target=device ${GRUB_CUSTOM_ACPI}` | sed -e "s/^/  /"
    cat << EOF
acpi (\$root)`make_system_path_relative_to_its_root ${GRUB_CUSTOM_ACPI}`
EOF
fi
```

Updated grub:

```
sudo update-grub

Generating grub configuration file ...
Found custom ACPI table: /boot/dsdt.aml
Found linux image: /boot/vmlinuz-4.0.5-040005-generic
Found initrd image: /boot/initrd.img-4.0.5-040005-generic
```

Reboot

```
sudo reboot
```

Decompile /sys/firmware/acpi/tables/DSDT and inspect resultant dsdt file to confirm changes have indeed been loaded by grub.

```
cd && sudo cp /sys/firmware/acpi/tables/DSDT ./dsdt.aml && sudo iasl -d ./dsdt.aml
```

The changes aren't in there what am I doing wrong here please?

---

