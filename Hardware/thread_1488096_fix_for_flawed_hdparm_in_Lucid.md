---
title: "fix for flawed hdparm in Lucid"
date: 2010-05-19
forum: Hardware
---

### Post by Pjotr123 on 2010-05-19
When your hard disk suffers from ceaseless clicking (parking and unparking), you can stop that by changing the settings of hdparm in Lucid. By adding some lines to /etc/hdparm.conf. But you can't use the "command line code" anymore in 10.04; you have to use a different code. As follows:

In the terminal:
```

gksudo gedit /etc/hdparm.conf

```

Add this piece of code:

```

/dev/sda {
    apm = 254
    apm_battery = 254
}

```

Then reboot. The endless clicking should have ceased.

There's a bug report on Launchpad as well:
[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/568120](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/568120)

---

### Post by Pjotr123 on 2010-05-23
I just improved the instruction in my previous message. With thanks to Jan Claeys from ubuntu-be. :)

---

### Post by stchman on 2011-02-23
> **Pjotr123 said:**
> When your hard disk suffers from ceaseless clicking (parking and unparking), you can stop that by changing the settings of hdparm in Lucid. By adding some lines to /etc/hdparm.conf. But you can't use the "command line code" anymore in 10.04; you have to use a different code. As follows:

In the terminal:
```

gksudo gedit /etc/hdparm.conf

```Add this piece of code:

```

/dev/sda {
    apm = 254
    apm_battery = 254
}

```Then reboot. The endless clicking should have ceased.

There's a bug report on Launchpad as well:
[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/568120](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/568120)

This worked for me.  The Load_Cycle_Count is now under control.

---

