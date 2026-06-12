---
title: "stalls on reboot and Buffer I/O Error on device sda, logical block 0"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by dkartik on 2006-09-21
Hey, I've had a few problems on my machine that I just can't seem to puzzle out.  First of, I'm running a P4 2.67 Ghz processor on an ASUS P5S800 motherboard.  It has 4 IDE connections and 2 SATA connections and I've used up all 4 IDE's but none of the SATA's.  I have 3 hard drives and a dvd drive in my machine.  The Ubuntu install is secondary to the windows hard drive on one of the cable, while the other hard drive, which is second to the dvd burner provides extra space for the windows install.

Now I can boot up fine, but I can't restart the machine from inside ubuntu, it just halts at the end of everything shutting down where it says system will now reboot.  Also, on startup, I get a bunch of errors that say:
```
Buffer I/O error on device sda, logical block 0
sda: assuming drive cache: write through
```
Now these errors just keep on repeating, so if I'm in the terminal, not the graphical display, they just keep on going non-stop, making it very difficult for me to follow what I have been typing.
I'm including my dmesg as well:
```
[17184434.544000] sda : READ CAPACITY failed.
[17184434.544000] sda : status=1, message=00, host=0, driver=08
[17184434.544000] sd: Current: sense key: No Sense
[17184434.544000]     Additional sense: No additional sense information
[17184434.800000] sda: test WP failed, assume Write Enabled
[17184434.800000] sda: assuming drive cache: write through
[17184434.800000]  sda:<4>printk: 1 messages suppressed.
[17184434.800000] Buffer I/O error on device sda, logical block 0
[17184434.800000]  unable to read partition table
[17184435.044000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184435.044000]    : Current: sense key: No Sense
[17184435.044000]     Additional sense: No additional sense information
[17184436.020000] sda: Unit Not Ready, sense:
[17184436.020000] : Current: sense key: No Sense
[17184436.020000]     Additional sense: No additional sense information
[17184436.792000] sda : READ CAPACITY failed.
[17184436.792000] sda : status=1, message=00, host=0, driver=08
[17184436.792000] sd: Current: sense key: No Sense
[17184436.792000]     Additional sense: No additional sense information
[17184437.048000] sda: test WP failed, assume Write Enabled
[17184437.048000] sda: assuming drive cache: write through
[17184437.292000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184437.292000]    : Current: sense key: No Sense
[17184437.292000]     Additional sense: No additional sense information
[17184438.028000] sda: Unit Not Ready, sense:
[17184438.028000] : Current: sense key: No Sense
[17184438.028000]     Additional sense: No additional sense information
[17184438.812000] sda : READ CAPACITY failed.
[17184438.812000] sda : status=1, message=00, host=0, driver=08
[17184438.812000] sd: Current: sense key: No Sense
[17184438.812000]     Additional sense: No additional sense information
[17184439.068000] sda: test WP failed, assume Write Enabled
[17184439.068000] sda: assuming drive cache: write through
[17184439.068000]  sda:<4>printk: 1 messages suppressed.
[17184439.068000] Buffer I/O error on device sda, logical block 0
[17184439.068000]  unable to read partition table
[17184439.312000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184439.312000]    : Current: sense key: No Sense
[17184439.312000]     Additional sense: No additional sense information
[17184440.288000] sda: Unit Not Ready, sense:
[17184440.288000] : Current: sense key: No Sense
[17184440.288000]     Additional sense: No additional sense information
[17184441.052000] sda : READ CAPACITY failed.
[17184441.052000] sda : status=1, message=00, host=0, driver=08
[17184441.056000] sd: Current: sense key: No Sense
[17184441.056000]     Additional sense: No additional sense information
[17184441.312000] sda: test WP failed, assume Write Enabled
[17184441.312000] sda: assuming drive cache: write through
[17184441.556000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184441.556000]    : Current: sense key: No Sense
[17184441.556000]     Additional sense: No additional sense information
[17184442.288000] sda: Unit Not Ready, sense:
[17184442.288000] : Current: sense key: No Sense
[17184442.288000]     Additional sense: No additional sense information
[17184443.056000] sda : READ CAPACITY failed.
[17184443.056000] sda : status=1, message=00, host=0, driver=08
[17184443.056000] sd: Current: sense key: No Sense
[17184443.056000]     Additional sense: No additional sense information
[17184443.332000] sda: test WP failed, assume Write Enabled
[17184443.332000] sda: assuming drive cache: write through
[17184443.332000]  sda:<4>printk: 1 messages suppressed.
[17184443.332000] Buffer I/O error on device sda, logical block 0
[17184443.332000]  unable to read partition table
[17184443.576000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184443.576000]    : Current: sense key: No Sense
[17184443.576000]     Additional sense: No additional sense information
[17184444.556000] sda: Unit Not Ready, sense:
[17184444.556000] : Current: sense key: No Sense
[17184444.556000]     Additional sense: No additional sense information
[17184445.324000] sda : READ CAPACITY failed.
[17184445.324000] sda : status=1, message=00, host=0, driver=08
[17184445.324000] sd: Current: sense key: No Sense
[17184445.324000]     Additional sense: No additional sense information
[17184445.580000] sda: test WP failed, assume Write Enabled
[17184445.580000] sda: assuming drive cache: write through
[17184445.824000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184445.824000]    : Current: sense key: No Sense
[17184445.824000]     Additional sense: No additional sense information
[17184446.556000] sda: Unit Not Ready, sense:
[17184446.556000] : Current: sense key: No Sense
[17184446.556000]     Additional sense: No additional sense information
[17184447.324000] sda : READ CAPACITY failed.
[17184447.324000] sda : status=1, message=00, host=0, driver=08
[17184447.324000] sd: Current: sense key: No Sense
[17184447.324000]     Additional sense: No additional sense information
[17184447.580000] sda: test WP failed, assume Write Enabled
[17184447.580000] sda: assuming drive cache: write through
[17184447.580000]  sda:<4>printk: 1 messages suppressed.
[17184447.580000] Buffer I/O error on device sda, logical block 0
[17184447.580000]  unable to read partition table
[17184448.580000] sda: Unit Not Ready, sense:
[17184448.580000] : Current: sense key: No Sense
[17184448.580000]     Additional sense: No additional sense information
[17184449.344000] sda : READ CAPACITY failed.
[17184449.344000] sda : status=1, message=00, host=0, driver=08
[17184449.344000] sd: Current: sense key: No Sense
[17184449.344000]     Additional sense: No additional sense information
[17184449.604000] sda: test WP failed, assume Write Enabled
[17184449.604000] sda: assuming drive cache: write through
[17184450.336000] sda: Unit Not Ready, sense:
[17184450.336000] : Current: sense key: No Sense
[17184450.336000]     Additional sense: No additional sense information
[17184451.104000] sda : READ CAPACITY failed.
[17184451.104000] sda : status=1, message=00, host=0, driver=08
[17184451.104000] sd: Current: sense key: No Sense
[17184451.104000]     Additional sense: No additional sense information
[17184451.360000] sda: test WP failed, assume Write Enabled
[17184451.360000] sda: assuming drive cache: write through
[17184451.360000]  sda: unable to read partition table
[17184451.604000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184451.604000]    : Current: sense key: No Sense
[17184451.604000]     Additional sense: No additional sense information
[17184454.284000] sda: Unit Not Ready, sense:
[17184454.284000] : Current: sense key: No Sense
[17184454.284000]     Additional sense: No additional sense information
[17184455.052000] sda : READ CAPACITY failed.
[17184455.052000] sda : status=1, message=00, host=0, driver=08
[17184455.052000] sd: Current: sense key: No Sense
[17184455.052000]     Additional sense: No additional sense information
[17184455.304000] sda: test WP failed, assume Write Enabled
[17184455.304000] sda: assuming drive cache: write through
[17184455.552000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184455.552000]    : Current: sense key: No Sense
[17184455.552000]     Additional sense: No additional sense information
[17184456.284000] sda: Unit Not Ready, sense:
[17184456.284000] : Current: sense key: No Sense
[17184456.284000]     Additional sense: No additional sense information
[17184457.052000] sda : READ CAPACITY failed.
[17184457.052000] sda : status=1, message=00, host=0, driver=08
[17184457.056000] sd: Current: sense key: No Sense
[17184457.056000]     Additional sense: No additional sense information
[17184457.312000] sda: test WP failed, assume Write Enabled
[17184457.312000] sda: assuming drive cache: write through
[17184457.312000]  sda:<4>printk: 3 messages suppressed.
[17184457.312000] Buffer I/O error on device sda, logical block 0
[17184457.312000]  unable to read partition table
[17184457.556000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184457.556000]    : Current: sense key: No Sense
[17184457.556000]     Additional sense: No additional sense information
[17184458.532000] sda: Unit Not Ready, sense:
[17184458.532000] : Current: sense key: No Sense
[17184458.532000]     Additional sense: No additional sense information
[17184459.320000] sda : READ CAPACITY failed.
[17184459.320000] sda : status=1, message=00, host=0, driver=08
[17184459.320000] sd: Current: sense key: No Sense
[17184459.324000]     Additional sense: No additional sense information
[17184459.580000] sda: test WP failed, assume Write Enabled
[17184459.580000] sda: assuming drive cache: write through
[17184459.824000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184459.824000]    : Current: sense key: No Sense
[17184459.824000]     Additional sense: No additional sense information
[17184460.556000] sda: Unit Not Ready, sense:
[17184460.556000] : Current: sense key: No Sense
[17184460.556000]     Additional sense: No additional sense information
[17184461.324000] sda : READ CAPACITY failed.
[17184461.324000] sda : status=1, message=00, host=0, driver=08
[17184461.324000] sd: Current: sense key: No Sense
[17184461.324000]     Additional sense: No additional sense information
[17184461.580000] sda: test WP failed, assume Write Enabled
[17184461.580000] sda: assuming drive cache: write through
[17184461.580000]  sda:<4>printk: 1 messages suppressed.
[17184461.584000] Buffer I/O error on device sda, logical block 0
[17184461.584000]  unable to read partition table
[17184461.828000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184461.828000]    : Current: sense key: No Sense
[17184461.828000]     Additional sense: No additional sense information
[17184462.804000] sda: Unit Not Ready, sense:
[17184462.804000] : Current: sense key: No Sense
[17184462.804000]     Additional sense: No additional sense information
[17184463.572000] sda : READ CAPACITY failed.
[17184463.572000] sda : status=1, message=00, host=0, driver=08
[17184463.572000] sd: Current: sense key: No Sense
[17184463.572000]     Additional sense: No additional sense information
[17184463.832000] sda: test WP failed, assume Write Enabled
[17184463.832000] sda: assuming drive cache: write through
[17184464.092000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184464.096000]    : Current: sense key: No Sense
[17184464.096000]     Additional sense: No additional sense information
[17184464.828000] sda: Unit Not Ready, sense:
[17184464.828000] : Current: sense key: No Sense
[17184464.828000]     Additional sense: No additional sense information
[17184465.596000] sda : READ CAPACITY failed.
[17184465.596000] sda : status=1, message=00, host=0, driver=08
[17184465.600000] sd: Current: sense key: No Sense
[17184465.600000]     Additional sense: No additional sense information
[17184465.856000] sda: test WP failed, assume Write Enabled
[17184465.856000] sda: assuming drive cache: write through
[17184465.856000]  sda:<4>printk: 1 messages suppressed.
[17184465.856000] Buffer I/O error on device sda, logical block 0
[17184465.856000]  unable to read partition table
[17184466.832000] sda: Unit Not Ready, sense:
[17184466.832000] : Current: sense key: No Sense
[17184466.832000]     Additional sense: No additional sense information
[17184467.604000] sda : READ CAPACITY failed.
[17184467.604000] sda : status=1, message=00, host=0, driver=08
[17184467.604000] sd: Current: sense key: No Sense
[17184467.604000]     Additional sense: No additional sense information
[17184467.856000] sda: test WP failed, assume Write Enabled
[17184467.856000] sda: assuming drive cache: write through
[17184468.592000] sda: Unit Not Ready, sense:
[17184468.592000] : Current: sense key: No Sense
[17184468.592000]     Additional sense: No additional sense information
[17184469.384000] sda : READ CAPACITY failed.
[17184469.384000] sda : status=1, message=00, host=0, driver=08
[17184469.384000] sd: Current: sense key: No Sense
[17184469.384000]     Additional sense: No additional sense information
[17184469.636000] sda: test WP failed, assume Write Enabled
[17184469.636000] sda: assuming drive cache: write through
[17184469.636000]  sda:<4>printk: 1 messages suppressed.
[17184469.636000] Buffer I/O error on device sda, logical block 0
[17184469.636000]  unable to read partition table
[17184469.880000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184469.880000]    : Current: sense key: No Sense
[17184469.880000]     Additional sense: No additional sense information
[17184472.540000] sda: Unit Not Ready, sense:
[17184472.540000] : Current: sense key: No Sense
[17184472.540000]     Additional sense: No additional sense information
[17184473.308000] sda : READ CAPACITY failed.
[17184473.308000] sda : status=1, message=00, host=0, driver=08
[17184473.308000] sd: Current: sense key: No Sense
[17184473.308000]     Additional sense: No additional sense information
[17184473.564000] sda: test WP failed, assume Write Enabled
[17184473.564000] sda: assuming drive cache: write through
[17184473.812000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184473.812000]    : Current: sense key: No Sense
[17184473.812000]     Additional sense: No additional sense information
[17184474.564000] sda: Unit Not Ready, sense:
[17184474.564000] : Current: sense key: No Sense
[17184474.564000]     Additional sense: No additional sense information
[17184475.332000] sda : READ CAPACITY failed.
[17184475.332000] sda : status=1, message=00, host=0, driver=08
[17184475.332000] sd: Current: sense key: No Sense
[17184475.332000]     Additional sense: No additional sense information
[17184475.588000] sda: test WP failed, assume Write Enabled
[17184475.588000] sda: assuming drive cache: write through
[17184475.588000]  sda:<4>printk: 1 messages suppressed.
[17184475.588000] Buffer I/O error on device sda, logical block 0
[17184475.588000]  unable to read partition table
[17184475.832000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184475.832000]    : Current: sense key: No Sense
[17184475.832000]     Additional sense: No additional sense information
[17184476.812000] sda: Unit Not Ready, sense:
[17184476.812000] : Current: sense key: No Sense
[17184476.812000]     Additional sense: No additional sense information
[17184477.580000] sda : READ CAPACITY failed.
[17184477.580000] sda : status=1, message=00, host=0, driver=08
[17184477.580000] sd: Current: sense key: No Sense
[17184477.580000]     Additional sense: No additional sense information
[17184477.836000] sda: test WP failed, assume Write Enabled
[17184477.836000] sda: assuming drive cache: write through
[17184478.080000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184478.080000]    : Current: sense key: No Sense
[17184478.080000]     Additional sense: No additional sense information
[17184478.816000] sda: Unit Not Ready, sense:
[17184478.816000] : Current: sense key: No Sense
[17184478.816000]     Additional sense: No additional sense information
[17184479.604000] sda : READ CAPACITY failed.
[17184479.604000] sda : status=1, message=00, host=0, driver=08
[17184479.604000] sd: Current: sense key: No Sense
[17184479.604000]     Additional sense: No additional sense information
[17184479.856000] sda: test WP failed, assume Write Enabled
[17184479.856000] sda: assuming drive cache: write through
[17184479.856000]  sda:<4>printk: 1 messages suppressed.
[17184479.856000] Buffer I/O error on device sda, logical block 0
[17184479.860000]  unable to read partition table
[17184480.836000] sda: Unit Not Ready, sense:
[17184480.836000] : Current: sense key: No Sense
[17184480.836000]     Additional sense: No additional sense information
[17184481.604000] sda : READ CAPACITY failed.
[17184481.604000] sda : status=1, message=00, host=0, driver=08
[17184481.604000] sd: Current: sense key: No Sense
[17184481.604000]     Additional sense: No additional sense information
[17184481.860000] sda: test WP failed, assume Write Enabled
[17184481.860000] sda: assuming drive cache: write through
[17184482.596000] sda: Unit Not Ready, sense:
[17184482.596000] : Current: sense key: No Sense
[17184482.596000]     Additional sense: No additional sense information
[17184483.364000] sda : READ CAPACITY failed.
[17184483.364000] sda : status=1, message=00, host=0, driver=08
[17184483.364000] sd: Current: sense key: No Sense
[17184483.364000]     Additional sense: No additional sense information
[17184483.620000] sda: test WP failed, assume Write Enabled
[17184483.620000] sda: assuming drive cache: write through
[17184483.620000]  sda:<4>printk: 1 messages suppressed.
[17184483.620000] Buffer I/O error on device sda, logical block 0
[17184483.620000]  unable to read partition table
[17184483.864000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184483.864000]    : Current: sense key: No Sense
[17184483.864000]     Additional sense: No additional sense information
[17184486.544000] sda: Unit Not Ready, sense:
[17184486.544000] : Current: sense key: No Sense
[17184486.544000]     Additional sense: No additional sense information
[17184487.312000] sda : READ CAPACITY failed.
[17184487.312000] sda : status=1, message=00, host=0, driver=08
[17184487.312000] sd: Current: sense key: No Sense
[17184487.312000]     Additional sense: No additional sense information
[17184487.568000] sda: test WP failed, assume Write Enabled
[17184487.568000] sda: assuming drive cache: write through
[17184487.812000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184487.812000]    : Current: sense key: No Sense
[17184487.812000]     Additional sense: No additional sense information
[17184488.544000] sda: Unit Not Ready, sense:
[17184488.544000] : Current: sense key: No Sense
[17184488.544000]     Additional sense: No additional sense information
[17184489.312000] sda : READ CAPACITY failed.
[17184489.312000] sda : status=1, message=00, host=0, driver=08
[17184489.312000] sd: Current: sense key: No Sense
[17184489.312000]     Additional sense: No additional sense information
[17184489.568000] sda: test WP failed, assume Write Enabled
[17184489.568000] sda: assuming drive cache: write through
[17184489.568000]  sda:<4>printk: 1 messages suppressed.
[17184489.568000] Buffer I/O error on device sda, logical block 0
[17184489.568000]  unable to read partition table
[17184489.836000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184489.836000]    : Current: sense key: No Sense
[17184489.836000]     Additional sense: No additional sense information
[17184490.812000] sda: Unit Not Ready, sense:
[17184490.812000] : Current: sense key: No Sense
[17184490.812000]     Additional sense: No additional sense information
[17184491.584000] sda : READ CAPACITY failed.
[17184491.584000] sda : status=1, message=00, host=0, driver=08
[17184491.584000] sd: Current: sense key: No Sense
[17184491.584000]     Additional sense: No additional sense information
[17184491.836000] sda: test WP failed, assume Write Enabled
[17184491.836000] sda: assuming drive cache: write through
[17184492.080000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184492.080000]    : Current: sense key: No Sense
[17184492.084000]     Additional sense: No additional sense information
[17184492.816000] sda: Unit Not Ready, sense:
[17184492.816000] : Current: sense key: No Sense
[17184492.816000]     Additional sense: No additional sense information
[17184493.584000] sda : READ CAPACITY failed.
[17184493.584000] sda : status=1, message=00, host=0, driver=08
[17184493.584000] sd: Current: sense key: No Sense
[17184493.584000]     Additional sense: No additional sense information
[17184493.840000] sda: test WP failed, assume Write Enabled
[17184493.840000] sda: assuming drive cache: write through
[17184493.840000]  sda:<4>printk: 1 messages suppressed.
[17184493.840000] Buffer I/O error on device sda, logical block 0
[17184493.840000]  unable to read partition table
[17184494.084000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184494.084000]    : Current: sense key: No Sense
[17184494.084000]     Additional sense: No additional sense information
[17184495.084000] sda: Unit Not Ready, sense:
[17184495.084000] : Current: sense key: No Sense
[17184495.084000]     Additional sense: No additional sense information
[17184495.852000] sda : READ CAPACITY failed.
[17184495.852000] sda : status=1, message=00, host=0, driver=08
[17184495.852000] sd: Current: sense key: No Sense
[17184495.852000]     Additional sense: No additional sense information
[17184496.108000] sda: test WP failed, assume Write Enabled
[17184496.108000] sda: assuming drive cache: write through
[17184496.352000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184496.352000]    : Current: sense key: No Sense
[17184496.352000]     Additional sense: No additional sense information
[17184497.088000] sda: Unit Not Ready, sense:
[17184497.088000] : Current: sense key: No Sense
[17184497.088000]     Additional sense: No additional sense information
[17184497.856000] sda : READ CAPACITY failed.
[17184497.856000] sda : status=1, message=00, host=0, driver=08
[17184497.856000] sd: Current: sense key: No Sense
[17184497.856000]     Additional sense: No additional sense information
[17184498.112000] sda: test WP failed, assume Write Enabled
[17184498.112000] sda: assuming drive cache: write through
[17184498.112000]  sda:<4>printk: 1 messages suppressed.
[17184498.112000] Buffer I/O error on device sda, logical block 0
[17184498.112000]  unable to read partition table
[17184498.356000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184498.356000]    : Current: sense key: No Sense
[17184498.356000]     Additional sense: No additional sense information
[17184499.336000] sda: Unit Not Ready, sense:
[17184499.336000] : Current: sense key: No Sense
[17184499.336000]     Additional sense: No additional sense information
[17184500.124000] sda : READ CAPACITY failed.
[17184500.124000] sda : status=1, message=00, host=0, driver=08
[17184500.124000] sd: Current: sense key: No Sense
[17184500.124000]     Additional sense: No additional sense information
[17184500.380000] sda: test WP failed, assume Write Enabled
[17184500.380000] sda: assuming drive cache: write through
[17184500.624000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184500.624000]    : Current: sense key: No Sense
[17184500.624000]     Additional sense: No additional sense information
[17184501.356000] sda: Unit Not Ready, sense:
[17184501.356000] : Current: sense key: No Sense
[17184501.356000]     Additional sense: No additional sense information
[17184502.124000] sda : READ CAPACITY failed.
[17184502.124000] sda : status=1, message=00, host=0, driver=08
[17184502.124000] sd: Current: sense key: No Sense
[17184502.124000]     Additional sense: No additional sense information
[17184502.384000] sda: test WP failed, assume Write Enabled
[17184502.384000] sda: assuming drive cache: write through
[17184502.384000]  sda: unable to read partition table
[17184502.628000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184502.628000]    : Current: sense key: No Sense
[17184502.628000]     Additional sense: No additional sense information
[17184503.604000] sda: Unit Not Ready, sense:
[17184503.604000] : Current: sense key: No Sense
[17184503.604000]     Additional sense: No additional sense information
[17184504.372000] sda : READ CAPACITY failed.
[17184504.372000] sda : status=1, message=00, host=0, driver=08
[17184504.372000] sd: Current: sense key: No Sense
[17184504.372000]     Additional sense: No additional sense information
[17184504.628000] sda: test WP failed, assume Write Enabled
[17184504.632000] sda: assuming drive cache: write through
[17184504.876000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184504.876000]    : Current: sense key: No Sense
[17184504.876000]     Additional sense: No additional sense information
[17184505.628000] sda: Unit Not Ready, sense:
[17184505.628000] : Current: sense key: No Sense
[17184505.628000]     Additional sense: No additional sense information
[17184506.396000] sda : READ CAPACITY failed.
[17184506.396000] sda : status=1, message=00, host=0, driver=08
[17184506.396000] sd: Current: sense key: No Sense
[17184506.396000]     Additional sense: No additional sense information
[17184506.652000] sda: test WP failed, assume Write Enabled
[17184506.652000] sda: assuming drive cache: write through
[17184506.652000]  sda:<4>printk: 3 messages suppressed.
[17184506.652000] Buffer I/O error on device sda, logical block 0
[17184506.652000]  unable to read partition table
[17184506.896000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184506.900000]    : Current: sense key: No Sense
[17184506.900000]     Additional sense: No additional sense information
[17184507.876000] sda: Unit Not Ready, sense:
[17184507.876000] : Current: sense key: No Sense
[17184507.876000]     Additional sense: No additional sense information
[17184508.648000] sda : READ CAPACITY failed.
[17184508.648000] sda : status=1, message=00, host=0, driver=08
[17184508.648000] sd: Current: sense key: No Sense
[17184508.648000]     Additional sense: No additional sense information
[17184508.916000] sda: test WP failed, assume Write Enabled
[17184508.916000] sda: assuming drive cache: write through
[17184509.148000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184509.148000]    : Current: sense key: No Sense
[17184509.148000]     Additional sense: No additional sense information
[17184509.880000] sda: Unit Not Ready, sense:
[17184509.880000] : Current: sense key: No Sense
[17184509.880000]     Additional sense: No additional sense information
[17184510.684000] sda : READ CAPACITY failed.
[17184510.684000] sda : status=1, message=00, host=0, driver=08
[17184510.684000] sd: Current: sense key: No Sense
[17184510.684000]     Additional sense: No additional sense information
[17184510.928000] sda: test WP failed, assume Write Enabled
[17184510.928000] sda: assuming drive cache: write through
[17184510.928000]  sda:<4>printk: 1 messages suppressed.
[17184510.928000] Buffer I/O error on device sda, logical block 0
[17184510.928000]  unable to read partition table
[17184511.196000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184511.196000]    : Current: sense key: No Sense
[17184511.196000]     Additional sense: No additional sense information
[17184512.152000] sda: Unit Not Ready, sense:
[17184512.152000] : Current: sense key: No Sense
[17184512.152000]     Additional sense: No additional sense information
[17184512.920000] sda : READ CAPACITY failed.
[17184512.920000] sda : status=1, message=00, host=0, driver=08
[17184512.920000] sd: Current: sense key: No Sense
[17184512.920000]     Additional sense: No additional sense information
[17184513.176000] sda: test WP failed, assume Write Enabled
[17184513.180000] sda: assuming drive cache: write through
[17184513.424000] sd 2:0:0:0: ioctl_internal_command return code = 8000002
[17184513.424000]    : Current: sense key: No Sense
[17184513.424000]     Additional sense: No additional sense information
[17184514.156000] sda: Unit Not Ready, sense:
[17184514.156000] : Current: sense key: No Sense
[17184514.156000]     Additional sense: No additional sense information
[17184514.928000] sda : READ CAPACITY failed.
[17184514.928000] sda : status=1, message=00, host=0, driver=08
[17184514.928000] sd: Current: sense key: No Sense
[17184514.928000]     Additional sense: No additional sense information
[17184515.180000] sda: test WP failed, assume Write Enabled
[17184515.180000] sda: assuming drive cache: write through
[17184515.180000]  sda:<4>printk: 1 messages suppressed.
[17184515.180000] Buffer I/O error on device sda, logical block 0
[17184515.180000]  unable to read partition table
```

The thing that boggles me, is I don't think I have an sda device installed.

Any help would be greatly appreciated.

---

### Post by dkartik on 2006-09-24
Bumping, can nobody help me?

---

### Post by nadamsieee on 2006-10-23
[http://www.ubuntuforums.org/showthread.php?t=276930](http://www.ubuntuforums.org/showthread.php?t=276930)

---

