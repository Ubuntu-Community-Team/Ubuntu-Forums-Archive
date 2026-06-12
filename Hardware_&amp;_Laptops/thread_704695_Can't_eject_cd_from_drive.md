---
title: "Can't eject cd from drive"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by badmotor on 2008-02-22
Burned a copy of Gutsy .iso last night, and it came up with errors (must've burnt it too fast).  Now I can't eject the cd, it says it is not mounted. Restarting the machine does nothing.

Heres the readout from mount:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by mgichoga on 2008-02-22
whats the output of the command 'fdisk -l' This should give you a listing of drives in your computer.

---

### Post by xeth_delta on 2008-02-22
Silly question, but have you tried issuing "eject" from the terminal?
Might be some program locking the drive, you can look it up with
```
lsof /dev/cdrom
```
or
```
lsof /dev/cdrom0
```

[edit] Besides, you can also check if the cd is mounted with "mount".

---

### Post by oldsoundguy on 2008-02-22
take a paper clip and unbend it part way.  On the front of the drive is a very small hole.  Firmly insert the clip in there.  You will feel resistance and that is good . PUSH.  The drive drawer will open slightly and you can pull the drawer open and remove the cd.

---

### Post by badmotor on 2008-02-22
> **xeth_delta said:**
> Silly question, but have you tried issuing "eject" from the terminal?
Might be some program locking the drive, you can look it up with
```
lsof /dev/cdrom
```
or
```
lsof /dev/cdrom0
```

[edit] Besides, you can also check if the cd is mounted with "mount".

that code doesn't do anything, and I posted the results of 'mount' above, can anyone tell me what it means?

---

### Post by badmotor on 2008-02-22
> **oldsoundguy said:**
> take a paper clip and unbend it part way.  On the front of the drive is a very small hole.  Firmly insert the clip in there.  You will feel resistance and that is good . PUSH.  The drive drawer will open slightly and you can pull the drawer open and remove the cd.

there is no hole in the front.

---

### Post by xeth_delta on 2008-02-22
> **badmotor said:**
> there is no hole in the front.

Let me see if I understand correctly. It's not only in Linux that you can't eject the CD, right? That is rather unusual. It's not very likely, but maybe you would be able to do something from the BIOS.

---

### Post by Ayuthia on 2008-02-22
Have you tried to eject the CD while the computer is rebooting or have you tried to mount the cdrom and then unmount it?

The information that you posted on mount does not look like anything related to the cdrom but I am sure that you already knew that.  All I can tell is that the first one is your partition that you are using to run Ubuntu, but the rest look like normal system mounts.

---

### Post by oldsoundguy on 2008-02-22
the only drives I have seen without the pin hole in the front are flip open type such as the Sony USB and it has an Open/Eject button. I am not talking a hole big enough to put your finger into .. it is very small on MOST optical drives.  My brother's LAPTOP even has one.

---

### Post by badmotor on 2008-02-22
Ah thankyou, there was a flap covering the pinhole. Managed to get the cd out and carry on.

Tried to burn the distro again at a very slow speed, but it happened again. Very frustrating.

---

### Post by xeth_delta on 2008-02-23
> **badmotor said:**
> Ah thankyou, there was a flap covering the pinhole. Managed to get the cd out and carry on.

Tried to burn the distro again at a very slow speed, but it happened again. Very frustrating.

Glad oldsoundguy advice worked.
Any errors? Are you using the regular desktop CD? You could try the alternate CD.

---

### Post by AvgUser on 2008-02-23
BadMotor:  It is possible your .ISO file is corrupt. Have you tried to D/L this from another source yet?  I would recommend getting the Torrent for your specific needs from [[Here]]("http://mirrors.easynews.com/linux/ubuntu-releases/7.10/") (or your favorite mirror) and make another attempt at burning the ISO.

In addition, it is possible your Burner has issues... If all else fails, try burning on another machine.

Good Luck!

---

### Post by oldsoundguy on 2008-02-23
I had issues trying to install from the live CD and had to get the system CD.  I also burned it at the slowest speed possible and from the iso file on my hard drive, not download and burn from the web. Then all went smoothly

For those that posted software solutions to the stuck disk.  All well and good IF the system had loaded and worked. AND all good solutions.
BUT, I have always look for a PHYSICAL reason that something does not work first.  That is the thing that goes wrong more often.  A bad IDE cable or, in sound, a bad cable of any kind.  Connection not secure.  When you stick you hands inside a computer box you can sometimes UNFIX something totally unrelated to what you are trying to fix.  Check the hardware before you check or blame  the software.

---

### Post by xeth_delta on 2008-02-23
I agree with AvgUser, there might be something wrong with your iso image. Information on how to check it before burning it to CD here: [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28#head-6788e413b69a8947c263c08d435f3e7fa8a3237d](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28#head-6788e413b69a8947c263c08d435f3e7fa8a3237d)

---

### Post by oldsoundguy on 2008-02-23
You also need to do the check sum on the file before you burn it (I have a program on a Windows box called Hash Calc that is really great for that and it is free.)
If the numbers do not match, don't bother firing up the burner.

---

### Post by badmotor on 2008-02-25
> **oldsoundguy said:**
> You also need to do the check sum on the file before you burn it (I have a program on a Windows box called Hash Calc that is really great for that and it is free.)
If the numbers do not match, don't bother firing up the burner.

Cool, yeah - I did the MD5sum (whatever it is called), and it returned the correct number, so I just presumed it would be all good. Guess I should try from another source. 

Was originally going for Ubuntu Studio, but then I realised I don't have a DVD burner :( .. if only it was 1ooMB smaller. Ah well.

Thanks for the advice everybody ):P   Will try a few of these suggestions.

---

### Post by badmotor on 2008-02-25
> **xeth_delta said:**
> Glad oldsoundguy advice worked.
Any errors? Are you using the regular desktop CD? You could try the alternate CD.

Yep, regular desktop cd. Only error was:  CD was burned with errors, attempt failed (or something similar)

---

