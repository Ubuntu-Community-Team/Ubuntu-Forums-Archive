---
title: "CanoScan N640P scanner undetected in Jaunty"
date: 2009-05-25
forum: Hardware
---

### Post by Cubytus on 2009-05-25
This topic is about an old-school parallel port scanner that's still functional. 

Problem is simple, whenever I launch XSane from the menu, it says it cannot detect any scanner. I know there were problems in all Ubuntu versions accessing parallel port scanners, and the best I could achieve with 8.04 was scanning a tiny bit of image before the scanner froze and blocked the parallel printer connected on it. Not very useful.

Using Jaunty, I'm subject to parallel port issues such as this one [http://ubuntuforums.org/showthread.php?p=734289]("http://ubuntuforums.org/showthread.php?p=734289").

If anybody knows how to operate this scanner in any way in Ubuntu, I would be glad to hear.

---

### Post by benyau on 2009-07-15
I hope you have resolved this.  If otherwise, please check out this old thread:

[http://ubuntuforums.org/showthread.php?t=686768](http://ubuntuforums.org/showthread.php?t=686768)

Cheers,
BY

---

### Post by Cubytus on 2009-08-28
Nope, it doesn't work.

 Is it because a printer is connected on the same port as the scanner?

---

### Post by kryo on 2009-10-03
bump. :-)

I also have an ancient Canoscan N640P which isn't being found by xsane.

Followed:
[http://ubuntuforums.org/showthread.php?t=686768](http://ubuntuforums.org/showthread.php?t=686768)

Going to check out:
[http://ubuntuforums.org/showthread.php?t=441915](http://ubuntuforums.org/showthread.php?t=441915)

```
ls -al /dev/parport0 
crw-rw---- 1 lp lp 99, 0 2009-10-02 22:54 /dev/parport0
```

```
$ id
uid=1000(username) gid=1000(username) groups=4(adm),7(lp),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(username)
```

Seems like I have permissions for the parallel port.

Ran `sudo xsane` and still couldn't detect my scanner.

Still trying, will comment if I dig something up. Meanwhile, anyone who's got this working on Intrepid, I'd really be happy to read your solution!

>> Skimming through the topic I mentioned earlier: 441915

In contrast to the topic, my scanner does no buzzing or any sign of life at all. I only see "life" when I power it up.

```
$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```
(note, example shows using `sudo`. same result with/out sudo.)

```
$ gpasswd -a username lp
```
(still no joy..)

:confused:

Reading: [http://ohioloco.ubuntuforums.org/showthread.php?t=1270174](http://ohioloco.ubuntuforums.org/showthread.php?t=1270174)

```
$ sudo sane-find-scanner
...
  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

```
$ dmesg | grep parport
[   16.579882] parport_pc 00:09: reported by Plug and Play ACPI
[   16.579913] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   18.755709] lp0: using parport0 (interrupt-driven).
```

```
$ sudo SANE_DEBUG_CANON_PP=255 scanimage
[sanei_debug] Setting debug level of canon_pp to 255.
[canon_pp] >> sane_init(0xbfc3f358, 0x804d520): sane-backends 1.0.19
[canon_pp] sane_init: >> ieee1284_find_ports
[canon_pp] sane_init: 0 << ieee1284_find_ports
[canon_pp] sane_init: 1 parallel port(s) found.
[canon_pp] sane_init: port parport0
[canon_pp] >> init_device
[canon_pp] init_device: [configuring options]
[canon_pp] init_device: configuring opt: num_options
[canon_pp] init_device: configuring opt: resolution
[canon_pp] init_device: configuring opt: colour mode
[canon_pp] init_device: configuring opt: bit depth
[canon_pp] init_device: configuring opt: tl-x
[canon_pp] init_device: configuring opt: tl-y
[canon_pp] init_device: configuring opt: br-x
[canon_pp] init_device: configuring opt: br-y
[canon_pp] init_device: configuring opt: calibrate
[canon_pp] init_device: done opts
[canon_pp] << init_device
[canon_pp] sane_init: ># Define which port to use if one isn't specified - you should only have<
[canon_pp] sane_init: ># one of these lines!<
[canon_pp] sane_init: ># This is the default port to be used - others will be detected<
[canon_pp] sane_init: >ieee1284 parport0<
[canon_pp] sane_init: Successfully parsed default scanner.
[canon_pp] sane_init: ><
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># Define the location of our pixel weight file, can begin with ~/ if needed.<
[canon_pp] sane_init: ># You can have as many of these as you like - lines with ports that don't exist<
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># will be ignored.<
[canon_pp] sane_init: >#<
[canon_pp] sane_init: ># Parameters are:<
[canon_pp] sane_init: ># calibrate /path/to/calibration-file port-name<
[canon_pp] sane_init: >#<
[canon_pp] sane_init: ># The format of port-name is dependant on your OS version.<
[canon_pp] sane_init: >#<
[canon_pp] sane_init: ># If a file isn't speficied, the default name will be<
[canon_pp] sane_init: ># ~/.sane/canon_pp-calibration-[port-name]<
[canon_pp] sane_init: ><
[canon_pp] sane_init: >calibrate ~/.sane/canon_pp-calibration-pp0 parport0<
[canon_pp] sane_init: calibrate line, calibrate ~/.sane/canon_pp-calibration-pp0 parport0
[canon_pp] sane_init: Finding scanner on port 'parport0'
[canon_pp] sane_init: Found!
[canon_pp] sane_init: Parsed cal, for port 'parport0', weight file is '~/.sane/canon_pp-calibration-pp0'.
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># calibrate /etc/sane/my_calibration parport1<
[canon_pp] sane_init: ><
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># Enable the next line if you're having trouble with ECP mode such as I/O<
[canon_pp] sane_init: ># errors.  Nibble mode is slower, but more reliable.<
[canon_pp] sane_init: ><
[canon_pp] sane_init: >force_nibble<
[canon_pp] sane_init: force_nibble requested.
[canon_pp] sane_init: ><
[canon_pp] sane_init: ># Set a default initialisation mode for each port.  Valid modes are:<
[canon_pp] sane_init: ># AUTO		(attempts to automatically detect by trying both methods)<
[canon_pp] sane_init: ># FB620P	(10101010 style.. also works for FB320P)<
[canon_pp] sane_init: ># FB630P	(11001100 style.. also works for FB330P, N340P, N640P)<
[canon_pp] sane_init: ><
[canon_pp] sane_init: >init_mode AUTO parport0<
[canon_pp] sane_init: Parsed init.
[canon_pp] sane_init: ># init_mode FB620P parport0<
[canon_pp] sane_init: ># init_mode FB630P parport0<
[canon_pp] detect_mode: Opening port parport0
[canon_pp] detect_mode: Claiming port.
[canon_pp] detect_mode: Port supports ECP-S.
[canon_pp] detect_mode: Port supports interrupts.
[canon_pp] detect_mode: Using ECP-S Mode
[canon_pp] detect_mode: Nibble mode force in effect.
[canon_pp] sane_init: >> initialise
[canon_pp] Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
[canon_pp] Timeout: Reply 2 (0x0c in 0x1f) - Status = 0x1f
[canon_pp] initialise: could not wake scanner
[canon_pp] sane_init: << 1 initialise
[canon_pp] sane_init: Couldn't contact scanner on port parport0. Probably no scanner there?
[canon_pp] << sane_init
[canon_pp] >> sane_get_devices (0xbfc3f3b8, 0)
[canon_pp] << sane_get_devices
scanimage: no SANE devices found
[canon_pp] >> sane_exit
[canon_pp] << sane_exit

```

> Ok I got it to recognize the scanner by hash marking the ieee1284 line in Canon_pp.conf and power cycling every time before I try to do something with it. I also disconnected an old turned off printer from the parallel port. Xsane comes up listing the fb620p and the scanner starts to scan but then hangs after a few seconds of scanning.

I did not have the same luck when commenting ieee1284.. :confused:

---

### Post by kryo on 2009-10-03
They say, when you can't beat it -- install windows.

Tried on a windows computer, and it seems there is a hardware problem with the scanner. Windows can not recognize it with drivers -- which explains why it wouldn't work on linux too.

I guess my ancient canoscan kicked the bucket. :(

---

### Post by Cubytus on 2009-10-04
Mine is perfectly fine under Windoes. I insist the problem lies with the neglected parallel port framework in Ubuntu, as it's still abnormal that advice given on the forums work for some, and don't for the majority.

---

### Post by ysingh on 2010-08-26
> **Cubytus said:**
> Nope, it doesn't work.

 Is it because a printer is connected on the same port as the scanner?

:popcorn:

---

### Post by ysingh on 2010-08-26
both printer and scanners are connected to usb port. Then what is solution?

---

### Post by Cubytus on 2010-08-26
The N640P is a ***parallel*** port scanner, not an USB one. Please stay on topic.

---

