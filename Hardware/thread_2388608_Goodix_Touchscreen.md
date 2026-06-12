---
title: "Goodix Touchscreen"
date: 2018-04-05
forum: Hardware
---

### Post by 3djake on 2018-04-05
Hello

I am trying to get the goodix touch screen to work on my tablet, its a generic brand.

the touch screen is a 12c device.
```
sudo ls /sys/bus/i2c/devices/
i2c-0		 i2c-12  i2c-6		  i2c-CPAK8963:00  i2c-INTCF1B:00   i2c-SASX9500:00
i2c-1		 i2c-2	 i2c-7		  i2c-GODX0911:00  i2c-INTCF1C:00   i2c-SMB0349:00
i2c-10		 i2c-3	 i2c-8		  i2c-INBC0000:00  i2c-JSA01212:00  i2c-SMSC3750:00
i2c-10EC5640:00  i2c-4	 i2c-9		  i2c-INT33F4:00   i2c-KXCJ9000:00  i2c-TBQ24296:00
i2c-11		 i2c-5	 i2c-BSBG0160:00  i2c-INT33FB:00   i2c-MAX17047:00

```

I am assuming i2c-GODX0911:00 is for the touch screen.

```
$ lsmod |grep goodix
goodix                 16384  0
$ dmesg |grep GODX0911
[    3.364229] i2c_hid i2c-GODX0911:00: HID over i2c has not been provided an Int IRQ
[    3.364660] i2c_hid: probe of i2c-GODX0911:00 failed with error -22
$ uname -a
Linux jacob-tablet 4.13.0-38-generic #43-Ubuntu SMP Wed Mar 14 15:20:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
$ sudo modinfo goodix
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/input/touchscreen/goodix.ko
license:        GPL v2
description:    Goodix touchscreen driver
author:         Bastien Nocera <hadess@hadess.net>
author:         Benjamin Tissoires <benjamin.tissoires@gmail.com>
srcversion:     1EE302CC426A4526DB59DAA
alias:          i2c:GDIX1001:00
alias:          acpi*:GDIX1001:*
depends:        
intree:         Y
name:           goodix
vermagic:       4.13.0-38-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

```

the alias here says GDIX instead of GODX, maybe I am using wrong module?

I recompiled the module with the alteration as the registers appear to be the same.

```
$dmseg|grep GODX
    3.372597] i2c_hid i2c-GODX0911:00: HID over i2c has not been provided an Int IRQ
[    3.372761] i2c_hid: probe of i2c-GODX0911:00 failed with error -22
[  266.905343] Goodix-TS i2c-GODX0911:00: ID 911, version: 1060
[  266.910837] Goodix-TS i2c-GODX0911:00: Invalid config, using defaults
[  266.911203] input: Goodix Capacitive TouchScreen as /devices/platform/80860F41:01/i2c-1/i2c-GODX0911:00/input/input7
[  266.913220] genirq: Flags mismatch irq 0. 00002001 (GODX0911:00) vs. 00015a00 (timer)
[  266.915794] Goodix-TS i2c-GODX0911:00: request IRQ failed: -16
[  266.968101] Goodix-TS: probe of i2c-GODX0911:00 failed with error -16

```

The kernel fails to probe the device, any ideas?

I think I figured out the I2C address and IRQ from taking a look at the source of the android drivers but as far as I know there is no way to tell the kernel without coding an entire module.
```
#define GTP_INT_PORT    133
gpio_direction_output(GTP_INT_PORT, client->addr == 0x14);

```

Thanks.

---

### Post by 3djake on 2018-04-13
Hello,

I figured out how to fix the touch screen.

Turns out my DSDT tables were using the wrong pins.

I followed the instructions from the kernel documentation to override the dsdt table
[https://www.kernel.org/doc/Documentation/acpi/initrd_table_override.txt]("https://www.kernel.org/doc/Documentation/acpi/initrd_table_override.txt")

fixed most of the remarks, compiled and added the the table to initrd and got the touch screen working.
Here is my new dsdt table
[https://github.com/3djake/TM800A510L_DSDT]("https://github.com/3djake/TM800A510L_DSDT")

I read the following discussion and discovered my tablet had the same issue
[https://markmail.org/message/mpqpmh225qtwckji#query:+page:1+mid:i5prjwnvhdxgp52c+state:results]("https://markmail.org/message/mpqpmh225qtwckji#query:+page:1+mid:i5prjwnvhdxgp52c+state:results")
I was able to use his commits as a reference to correct my own
[https://git.ao2.it/Teclast-X98-Air-3G_C6J6_custom_DSDT.git/]("https://git.ao2.it/Teclast-X98-Air-3G_C6J6_custom_DSDT.git/")

Hopefully this is enough to help some one else.

Regards, Jake.

---

