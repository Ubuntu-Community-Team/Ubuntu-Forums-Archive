---
title: "Custom DSDT Without recompiling?"
date: 2018-04-08
forum: Hardware
---

### Post by 3djake on 2018-04-08
Hello,

I am trying to use a customised DSDT table without recompiling the kernel.

My kernel has CONFIG_ACPI_TABLE_UPGRADE=y

Lubuntu 17.10
```
uname -a
Linux jacob-tablet 4.13.0-38-generic #43-Ubuntu SMP Wed Mar 14 15:20:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```
#! /bin/sh -e

# Uncomment to load custom ACPI table
GRUB_CUSTOM_ACPI="/boot/dsdt.aml"

# DON'T MODIFY ANYTHING BELOW THIS LINE!

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

#. /usr/share/grub/grub-mkconfig_lib
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

```
#update-grub2
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found custom ACPI table: /boot/dsdt.aml
Found linux image: /boot/vmlinuz-4.13.0-38-generic
Found initrd image: /boot/initrd.img-4.13.0-38-generic
Found linux image: /boot/vmlinuz-4.13.0-21-generic
Found initrd image: /boot/initrd.img-4.13.0-21-generic
Adding boot menu entry for EFI firmware configuration
done

```

Am I doing this correctly, my custom tables are not loading.

EDIT: the best way I found was in the kernel documentation  Documentation/acpi/initrd_table_override.txt

Thanks

---

