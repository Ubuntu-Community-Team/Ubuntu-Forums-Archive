---
title: "Helping Getting the brother MFC-7360 to scan in 11.10"
date: 2012-01-04
forum: Hardware
---

### Post by BrantlyMedders on 2012-01-04
Greetings all,

I'm having some issues getting my Brother MFC-7360N to scan in 11.10 64 bit.

Here's what I have done thus far:

1.  Installed brscan4 and brscan-skey 64 bit.
2.  Followed [these directions]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101"), aside from I created symbolic links rather than copying the files.
3. Followed [these directions]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10") to ensure normal users could access the scanner.  I also made the edits in /lib/udev/rules.d/50-udev-default.rules suggested for Ubuntu 9.04.
4. Added brscan-skey to Autostart.
5. Rebooted the system.  I still cannot use the scanner as a normal user or as a superuser.

6.  lsusb shows the following output:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f9:0270 Brother Industries, Ltd 
Bus 005 Device 002: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse

```

7.  sane-find-scanner shows the following output:
```

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04f9, product=0x0270) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

8.  brscan-skey -l shows no output.

9.  The printer functions are working fine on the MFC-7360N, so I know the machine is working.

Could anyone please help me diagnose this issue?

---

### Post by demonipuch on 2012-01-05
Hello

You need to copy a few files in /usr/lib/sane :

```
sudo cp /usr/lib64/sane/libsane-brother4.so.1.0.7 /usr/lib/sane
sudo cp /usr/lib64/sane/libsane-brother4.so /usr/lib/sane
sudo cp /usr/lib64/sane/libsane-brother4.so.1 .usr/lib/sane
```

edit : nevermind, i didn't see that you created symlinks

---

### Post by nozyczek on 2012-01-13
> **BrantlyMedders said:**
> 
Could anyone please help me diagnose this issue?

BrantlyMedders,
Did you solve it yet? I'm having same problems.
Everything works under 10.04.3 64bit but not in 11.10 64 bit.
I tested it in 11.10 32 bit and it works there too. So I have no idea what is going on.

---

