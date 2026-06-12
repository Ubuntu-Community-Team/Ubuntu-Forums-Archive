---
title: "HDD and Video Resolution problems"
date: 2009-12-02
forum: Hardware
---

### Post by Enforcer83 on 2009-12-02
I recently reinstalled unbuntu using 9.10 amd64 distribution.

I installed Envy-NG and NTFS Configuration tools to aid in the setting up the desktop to my desired preferences.

When I tried to mount a 1TB - 4GB Drive,  the tool gave me this error

```
Failed to mount '/dev/sdb2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

This Drive is not raided.  I intend on trying the first option later.  If that doesn't work, what may be my problem?

For my second issue, simply put I cannot save my screen resolution the nVidia X Server Settings application when I run

```
sudo nvidia-settings
```

How can I work around this problem?

---

