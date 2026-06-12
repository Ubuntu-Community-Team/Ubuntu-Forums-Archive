---
title: "Pentax DSMobile 600 scanner detected but not working"
date: 2010-05-30
forum: Hardware
---

### Post by dakkar9999 on 2010-05-30
Well, I'm trying to get my Pentax DS Mobile 600 scanner to work.  I went to the SANE page [http://www.sane-project.org/sane-mfgs.html#Z-PENTAX](http://www.sane-project.org/sane-mfgs.html#Z-PENTAX) and according to a scanner probe (sudo sane-find-scanner)it seems to be detected.  Here's the log.


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0a17 [PENTAX], product=0x3210 [DSMobile 600], chip=GL841) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
sebastien@ontherun:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

The SANE page mentionned the GENESYS AND SANE-GENESYS packages which do not seem to be in the synaptic repository.

Any suggestions?

Thanks!

---

### Post by dakkar9999 on 2010-06-06
Bump.

---

### Post by netnode on 2010-06-07
bump from me also.

I can't even get the DC Mobile USB scanner detected.

---

### Post by f1aw on 2011-06-30
Have any one of you tried the [libsane]("http://packages.ubuntu.com/search?keywords=libsane") package? The [sane-genesys]("http://www.sane-project.org/man/sane-genesys.5.html") page lists the scanner model, so it has got to be supported.

Here is the ubuntu man-page for the [libsane]("http://manpages.ubuntu.com/manpages/lucid/man5/sane-genesys.5.html") package. And if all else fails you can compile the latest version from the GIT source available from debian servers "git://git.debian.org/sane/sane-backends.git".

---

