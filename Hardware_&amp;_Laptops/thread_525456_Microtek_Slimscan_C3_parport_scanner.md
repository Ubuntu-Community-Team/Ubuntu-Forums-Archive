---
title: "Microtek Slimscan C3 parport scanner"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by vze2jdnz on 2007-08-14
Hi, I'm fairly new to Linux and would really like to switch over from Windows.
I am running Kubuntu 7.04 and can not get my scanner to work at all.
According to the Sane homepage my scanner is supported.

I tried  sane-find-scanner -p  and get:

  # No Mustek parallel port scanners found. If you expected something
  # different, make sure the scanner is correctly connected to your computer
  # and you have apropriate access rights.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

When I try  scanimage -L  I get:

device `v4l:/dev/video0' is a Noname Elitegroup ECS TVP3XP FM1236 Tu virtual device

which is my TV tuner card.  I looked in the /dev/video0 file, but it is empty with zero bytes.

 I know the scanner is good because it works perfectly in Windows.

I am totally lost as I am really new to Linux and would really appreciate any help.

Thanks in advance!

---

### Post by vze2jdnz on 2007-08-27
Anyone... ?

---

### Post by quadomatic on 2007-08-29
I have this same scanner and I can't get it to work in Linux either.

Can anyone help?

---

### Post by geraldm on 2007-08-30
Note: I do not have this scanner, and cannot help much.

Parallel port scanners are difficult to detect, so for some scanners, just skip detection, 
Read the man pages for sane-microtek2, and be sure the necessary SCSI module is loaded.
Do try to set the environment variables, including SANE_DEBUG_MICROTEK2=128

You may have to experiment with a frontend like xsane to provide a scanning command.
A command line program like scanimage might also work.  

Sorry I do not know details about what command works for the scan.  
Note that that backend is listed as unmaintained.  You might try a post to the sane-devel
mailing list before giving up hope. 

Gerald

---

