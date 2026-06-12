---
title: "Epson NX130, printing works, but can't scan"
date: 2012-07-06
forum: Hardware
---

### Post by ubnewbie2 on 2012-07-06
I have an Epson NX130 printer/scanner.  I downloaded the printer drivers from Epson, and it was autodetected and works perfectly (in 12.04).

However Simplescan detects no scanners. The relevent part of sane-find-scanner's output is

```
found USB scanner (vendor=0x04b8, product=0x0883) at libusb:001:013
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```

and

```
scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

I found a reference which said to put the vendor/product code in /etc/sane.d/epson2.conf,   but no effect.  I tried to restart saned but
found it would not start and the /etc/default/saned contains

```
# Set to yes to start saned
RUN=no
```

So, I am quite lost now.  Can anyone help please?

Edit:  found it listed on the sane project site as

```
Stylus NX130 Series	USB	0x04b8/0x0883	Complete	all-in-one
```

but the link they give to  [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/) has the driver

```
epson-inkjet-printer-201101w_1.0.0-1lsb3.2_i386.deb
```

which is the one I already installed.

---

### Post by ubnewbie2 on 2012-07-07
Well, I have progress.

It is now recognised if I run as root.  In fact I can even

```
sudo scanimage>test.pnm
```

and it works.

So, maybe a permissions problem?  Does this mean tackling udev (something I haven't done before)?

---

### Post by ubnewbie2 on 2012-07-07
Eventually figured this out.  A rule somewhere was making the NX130 permissions owner=root, group=lp.  

I guess that makes sense, as it is a printer, AND a scanner.  Funny thing is, even though my user was not a member of lp , I was still able to print.  Making my user a member of lp has enabled me to use the scanner however.

I am not arguing too much, as long as it works :)

---

### Post by stevjen on 2012-11-12
> **ubnewbie2 said:**
> I have an Epson NX130 printer/scanner.  I downloaded the printer drivers from Epson, and it was autodetected and works perfectly (in 12.04).

However Simplescan detects no scanners. The relevent part of sane-find-scanner's output is

```
found USB scanner (vendor=0x04b8, product=0x0883) at libusb:001:013
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```and

```
scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```I found a reference which said to put the vendor/product code in /etc/sane.d/epson2.conf,   but no effect.  I tried to restart saned but
found it would not start and the /etc/default/saned contains

```
# Set to yes to start saned
RUN=no
```So, I am quite lost now.  Can anyone help please?

Edit:  found it listed on the sane project site as

```
Stylus NX130 Series    USB    0x04b8/0x0883    Complete    all-in-one
```but the link they give to  [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/) has the driver

```
epson-inkjet-printer-201101w_1.0.0-1lsb3.2_i386.deb
```which is the one I already installed.

I tried this and still can't get scanner to work. Wonder what I'm doing wrong?:(

---

### Post by stevjen on 2012-11-13
> **ubnewbie2 said:**
> Well, I have progress.

It is now recognised if I run as root.  In fact I can even

```
sudo scanimage>test.pnm
```and it works.

So, maybe a permissions problem?  Does this mean tackling udev (something I haven't done before)?

I have this problem!  How do I put that code in? I'm a newbie too.

---

### Post by ubnewbie2 on 2012-11-13
> **stevjen said:**
> I have this problem!  How do I put that code in? I'm a newbie too.

You type it into the terminal.  Just run Terminal from the dashboard the type the command in at the prompt. It will ask for your password, because of the 'sudo' at the start.

---

### Post by robin mcfarlane on 2013-01-02
Greetings. I similarly have the same printer NX130 that prints and copies but cannot scan. Have tried entering the below into the terminal without success. Any advice to a novice will be welcome. Cheers, Rob.

sudo scanimage>test.pnm

---

