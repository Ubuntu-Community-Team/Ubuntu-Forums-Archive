---
title: "SANE problem needs permissions setting"
date: 2009-05-30
forum: Hardware
---

### Post by David Brant on 2009-05-30
Hello

My Hewlet Packard ScanJet 4p (SCSI) only works if i temporarily set the current permissions each time i boot by typing:

```
sudo chmod a+r,a+w /dev/sg2

```
based on the following info.

```
david@david-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

david@david-desktop:~$ sudo scanimage -L
device `hp:/dev/sg2' is a Hewlett-Packard C1130A flatbed scanner

david@david-desktop:~$ sane-find-scanner -q

david@david-desktop:~$ sudo sane-find-scanner -q
found SCSI processor "HP C1130A 3614" at /dev/sg2

david@david-desktop:~$ ls -l /dev/sg2
crw-rw---- 1 root root 21, 2 2009-05-29 14:08 /dev/sg2
```

I believe the original command gives all users permission to access the scanner. However, i would like to make the changes (originally established on installation and subsequently when the system is booted) permanent. I am under the impression this might be possible by making changes to the 'udev rules' (or something like that). Unfortunately i have no experience at this.

Could anyone please suggest an permanent fix, preferably for all users please?

Dave

---

