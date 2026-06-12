---
title: "My computer has gone crazy!"
date: 2008-05-10
forum: Hardware
---

### Post by jamieh on 2008-05-10
OK here's the problem:

When I turn on my computer, it gets stuck at the POST screen, I press RESET, it happens again, after a few more Resets, it boots fine. Here is a video if you still don't understand. Please take the time to watch it and help me!

[http://ca.youtube.com/watch?v=_1-xs_RzjTo](http://ca.youtube.com/watch?v=_1-xs_RzjTo)

Do I need a new PSU?

Thanks!

---

### Post by kurtpete on 2008-05-10
This is more than likely a hardware issue (and nothing to do with any installed OS-es) since your machine is still in the middle of the POST sequence.  I would probably suspect:

1. power supply
2. hard drive (gearing up for failure)

...and in that order.  I've seen a power supply going bad do some pretty strange things.

---

### Post by jamieh on 2008-05-10
> **kurtpete said:**
> This is more than likely a hardware issue (and nothing to do with any installed OS-es) since your machine is still in the middle of the POST sequence.  I would probably suspect:

1. power supply
2. hard drive (gearing up for failure)

...and in that order.  I've seen a power supply going bad do some pretty strange things.

Both my PSU and hard-drives are quite old, I wouldn't be surprised if they need to be replaced. How can I be 100% sure what to replace, though?

---

### Post by information_entropy on 2008-05-10
The computer in the video has a 60 gig and a 30 gig Diamond Max hard drive.
I think both are S.M.A.R.T.  capable.

Install smart monitor tools

```
apt-get install smartmontools
```

Then run the following:

```

smartctl -H /dev/sda

smartctl -i /dev/sda

smartctl -A /dev/sda

```

That should read the information from the drives
and tell you if they are ok

```
man smartctl
```

will explain all of the command options.

Those smartctl commands all need sudo in front of them.
Read the man page first if that makes you nervous.

---

### Post by jamieh on 2008-05-10
> The computer in the video has a 60 gig and a 30 gig Diamond Max hard drive.

I made the video, it's my computer.

---

### Post by jamieh on 2008-05-10
> **information_entropy said:**
> run the following:

```

smartctl -H /dev/sda

smartctl -i /dev/sda

smartctl -A /dev/sda

```

Here's the output:
```
jamie@jamie-ubuntu:~$ sudo smartctl -H /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

SMART Health Status: OK
jamie@jamie-ubuntu:~$ sudo smartctl -i /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Device: ST380021 A                Version: 0811
Device type: disk
Local Time is: Sat May 10 20:04:02 2008 PDT
Device does not support SMART
jamie@jamie-ubuntu:~$ sudo smartctl -A /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

jamie@jamie-ubuntu:~$ 
```

---

### Post by bukwirm on 2008-05-10
> **jamieh said:**
> Both my PSU and hard-drives are quite old, I wouldn't be surprised if they need to be replaced. How can I be 100% sure what to replace, though?

Replace one of them; if that doesn't fix the problem, replace the other.

---

### Post by information_entropy on 2008-05-10
Well according to my spare brain “Google” 
Maxtor 6Y060L0 and 6E030L0 both support SMART.

On some machines it has to be enabled in the BIOS.

Check your BIOS configuration and see if the option exists,
and if it is enabled.

---

### Post by kurtpete on 2008-05-11
> **jamieh said:**
> Both my PSU and hard-drives are quite old, I wouldn't be surprised if they need to be replaced. How can I be 100% sure what to replace, though?

No easy (or cheap) way to know 100% of which I'm aware.  As mentioned, try swapping one out.  If you've got another machine with a compatible psu (or could borrow one from a friend or something) you can either determine that is the issue, or eliminate it as the cause.

If the above isn't an option, you might also try disconnecting a couple of components (if possible).  For instance the CD/DVD drives you have and potentially the non-booting drive.  There is certainly a spike on the psu during the boot process, and if your issue doesn't repeat itself with less of a load, it could be a good indication the psu is the problem (although that doesn't eliminate the fact you may have disconnected a failing drive).

---

### Post by jamieh on 2008-05-11
> **kurtpete said:**
> try swapping one out

If all of the drives aren't connected, GRUB Error-21's me. Damn bootloaders.

---

### Post by jamieh on 2008-05-11
> **bukwirm said:**
> Replace one of them; if that doesn't fix the problem, replace the other.

I'm not made of money.

---

### Post by RJARRRPCGP on 2008-05-11
That message is bogus, because ALL HDDs made in the 2000s have SMART. 

Even 1999s have SMART! LOL. 

Also, Maxtor 6E0xxxx HDDs are known to just fail. 

The 6E030L0s are one of the worst.

The false message may be caused by a bad HDD.

The other Maxtor, hopefully is OK.

---

### Post by jamieh on 2008-05-11
It still does it when the 30GB drive, and both my CD drives are unplugged.

---

### Post by RJARRRPCGP on 2008-05-11
Your 30 GB is more likely the cause. The 30 GB is 6E030L0. 
The 6E030L0s seem to have problems with having a high failure rate.

The 60 GB should be fine.

---

