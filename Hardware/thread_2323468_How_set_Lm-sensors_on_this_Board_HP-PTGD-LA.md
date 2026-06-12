---
title: "How set Lm-sensors on this Board HP-PTGD-LA"
date: 2016-05-05
forum: Hardware
---

### Post by sed_faster on 2016-05-05
Hello everyone,

I have this board: ([http://support.hp.com/us-en/document/c00361570#AbT1](http://support.hp.com/us-en/document/c00361570#AbT1)). And install ubuntu server 14.04LTS 32bits.

```
Linux fgedsc 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:27 UTC 2016 i686 i686 i686 GNU/Linux
```

I am trying monitor the temperature of the CPU with the program lm-sensors but although I ran command "sensors-detect" and chosen Yes all option this message appear when I ran command "sensors":

```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

The output the command "sensors-detect" it is:

```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:en",
	LC_ALL = (unset),
	LC_PAPER = "pt_PT.UTF-8",
	LC_ADDRESS = "pt_PT.UTF-8",
	LC_MONETARY = "pt_PT.UTF-8",
	LC_NUMERIC = "pt_PT.UTF-8",
	LC_TELEPHONE = "pt_PT.UTF-8",
	LC_IDENTIFICATION = "pt_PT.UTF-8",
	LC_MEASUREMENT = "pt_PT.UTF-8",
	LC_TIME = "pt_PT.UTF-8",
	LC_NAME = "pt_PT.UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# System: HP Pavilion 061 PX665AA-AB9 t3040.pt [0qz0211RE101PUFF200]
# Board: ASUSTeK Computer INC. Puffer2

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     Yes
Found `SMSC DME1737 Super IO'                               
    (hardware monitoring capabilities accessible via SMBus only)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): yes
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.
```

How can I resolve this problem?
Thanks

---

### Post by Yellow Pasque on 2016-05-06
Try this:
```
sudo modprobe -v dme1737
sensors
```

If it does not work, check dmesg:
```
dmesg | tail
```

You may have to add a boot parameter to make the module correctly:
[https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/478762/comments/7](https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/478762/comments/7)
Note that this may cause instability on some systems, which is why it was disabled by default.

---

### Post by sed_faster on 2016-05-07
> **Temüjin said:**
> Try this:
```
sudo modprobe -v dme1737
sensors
```

If it does not work, check dmesg:
```
dmesg | tail
```

You may have to add a boot parameter to make the module correctly:
[https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/478762/comments/7](https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/478762/comments/7)
Note that this may cause instability on some systems, which is why it was disabled by default.

Hello thanks to your help,
This is my file grub, before changes:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

According this link ([https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/478762/comments/7](https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/478762/comments/7)) I changed this line:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_enforce_resources=lax quiet splash"
```

Before changes this document the output of your command was:

```

**[B]er**@**df**:~$ sudo modprobe -v dme1737[/B]
insmod /lib/modules/4.2.0-27-generic/kernel/drivers/hwmon/hwmon-vid.ko 
insmod /lib/modules/4.2.0-27-generic/kernel/drivers/hwmon/dme1737.ko
**[B]er**@**df**:~$ sensors[/B]
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
**[B]er**@**df**:~$ dmesg | tail[/B]
[   20.699545] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[   21.138466] audit: type=1400 audit(1462644848.633:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=838 comm="apparmor_parser"
[   21.138492] audit: type=1400 audit(1462644848.633:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=838 comm="apparmor_parser"
[   21.138511] audit: type=1400 audit(1462644848.633:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=838 comm="apparmor_parser"
[   21.139713] audit: type=1400 audit(1462644848.633:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=838 comm="apparmor_parser"
[   21.376170] floppy0: no floppy controllers found
[   21.376191] work still pending
[   21.976912] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   22.004062] NFSD: starting 90-second grace period (net c1a9a5c0)
[   22.391906] init: plymouth-upstart-bridge main process (203) killed by TERM signal

```

After changes:

```

**er@df:~$ sudo modprobe -v dme1737**
insmod /lib/modules/4.2.0-27-generic/kernel/drivers/hwmon/hwmon-vid.ko 
insmod /lib/modules/4.2.0-27-generic/kernel/drivers/hwmon/dme1737.ko 
**er@df:~$ sensors**
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
**er@df:~$ dmesg | tail**
[   21.608738] audit: type=1400 audit(1462644281.825:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=803 comm="apparmor_parser"
[   21.609959] audit: type=1400 audit(1462644281.825:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=803 comm="apparmor_parser"
[   21.920079] floppy0: no floppy controllers found
[   21.920100] work still pending
[   22.524135] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   22.566526] NFSD: starting 90-second grace period (net c1a9a5c0)
[   23.173433] init: plymouth-upstart-bridge main process ended, respawning
[   51.035900] ACPI Warning: SystemIO range 0x0000000000000400-0x000000000000041F conflicts with OpRegion 0x0000000000000400-0x000000000000040F (\SMRG) (20150619/utaddress-254)
[   51.035919] ACPI Warning: SystemIO range 0x0000000000000400-0x000000000000041F conflicts with OpRegion 0x0000000000000400-0x000000000000040F (\_SB_.PCI0.SBRG.SMRG) (20150619/utaddress-254)
[   51.035931] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

```

I don't know interpret the output. That is why any help will be welcome, thanks

---

### Post by Yellow Pasque on 2016-05-07
Maybe instead of dme1737, you can use:
```
sudo modprobe -v asus_atk0110
```

---

