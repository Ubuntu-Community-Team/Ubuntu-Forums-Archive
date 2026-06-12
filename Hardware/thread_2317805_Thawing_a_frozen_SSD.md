---
title: "Thawing a frozen SSD"
date: 2016-03-19
forum: Hardware
---

### Post by Mr Fredrick on 2016-03-19
I am attempting to Secure Erase a Corsair Neutron XT 500GB SSD using 'hdparm' but I have been unsuccessful because the drive is always frozen even after a hot swap or a system suspend.

The Corsair is in my secondary drive bay that used to hold the DVD.

Can anybody give me some advice as to how I can 'unfreeze' the drive.

Thanks in advance,

MrFred. 

PS. My OS is Ubuntu 15.10 and my systems hardware is shown in my signature below.

---

### Post by QIII on 2016-03-20
So do you mean you are seeing something like this

```


Security: 
        Master password revision code = 65534
                supported
                enabled
        not     locked
                frozen
        not     expired: security count
                supported: enhanced erase
        Security level high
        2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT.
```

when you run 

```
hdparm -I /dev/sdX
```

---

### Post by Mr Fredrick on 2016-03-20
> So do you mean you are seeing something like this

Yes, below is (part of) the output I get:

```
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT. 
Checksum: correct
```

No matter what I attempt I can't get it to be NOT FROZEN!

---

### Post by QIII on 2016-03-20
Do you have your mobo set to allow hot swapping of disks?

---

### Post by Mr Fredrick on 2016-03-20
> **QIII said:**
> Do you have your mobo set to allow hot swapping of disks?

I THINK I do, at least the system doesn't complain if I pull the drive in and out, but how can I check to be sure that it does allow shot swapping?

---

### Post by QIII on 2016-03-20
Then you can hot swap.

CAVEATS for the following suggestion:  It may crash the kernel or it may brick the SSD permanently.

Some BIOSes/EFIs issue a "freeze command" at startup freezing all attached drives.

If you are looking at that output from hdparm right now (if not, get back there), you can sometimes "trick" the machine into complying by unplugging the data and power cables on the drive you are trying to clear momentarily and then plugging them back in.  Then issue

```
hdparm -I /dev/sdX
```

again and see if it is unfrozen.

Effectively, you are hot-swapping right in the middle of the process.

---

### Post by Mr Fredrick on 2016-03-20
> If you are looking at that output from hdparm right now (if not, get back there), you can sometimes "trick" the machine into complying by unplugging the data and power cables momentarily and then plugging them back in.

I've pulled the drive in and out of its bay quickly (and sometimes slowly) many times but it still remains frozen. I'm now at a loss as to what to do next!

---

### Post by QIII on 2016-03-20
Unfortunately that's all I have ever been able to find as a possible fix, and it has worked for me several times.

Maybe someone else has discovered something else.

---

### Post by Mr Fredrick on 2016-03-20
> Unfortunately that's all I have ever been able to find as a possible fix, and it has worked for me several times.

Thanks for the help anyway QIII.

---

### Post by mc4man on 2016-03-20
Have you looked at PartedMagic? [https://partedmagic.com/](https://partedmagic.com/)

---

### Post by QIII on 2016-03-20
Erasing an SSD is different than erasing an HDD.

---

### Post by mc4man on 2016-03-20
> **QIII said:**
> Erasing an SSD is different than erasing an HDD.

Pm has support for ssd secure erase   & some methods to 'unfreeze'  (sleep,  alt  sleep
on site doc [https://partedmagic.com/secure-erase/](https://partedmagic.com/secure-erase/)

---

### Post by sudodus on 2016-03-20
> **mc4man said:**
> Pm has support for ssd secure erase   & some methods to 'unfreeze'  (sleep,  alt  sleep
on site doc [https://partedmagic.com/secure-erase/](https://partedmagic.com/secure-erase/)

Thanks for this tip :-)

---

### Post by QIII on 2016-03-20
> **mc4man said:**
> Pm has support for ssd secure erase   & some methods to 'unfreeze'  (sleep,  alt  sleep
on site doc [https://partedmagic.com/secure-erase/](https://partedmagic.com/secure-erase/)

Very nice -- didn't realize that was there.

---

### Post by Mr Fredrick on 2016-03-21
Just to let you know the outcome of the attempt to thaw the Corsair SSD.

I downloaded Parted Magic and booted my machine from it and it reported that both my Corsair and Samsung SSDs were frozen. I therefore allowed it to do its "sleep mode" trick to unfreeze them and it worked but only for the Samsung, the Corsair remained frozen. It seems the Corsair is not only frozen but its also cooked (i.e. FAILED) so that it that. Its only 6 months old.

Pity there isn't a way to erase a failed or about to fail drive.

Anyway thanks for the help everybody.

---

### Post by oldfred on 2020-06-11
See hdparm and the --dco-freeze parameter.
It really just gives more info.

But then it is either the UEFI/BIOS or operating system protecting your system.
May be a non-obvious setting in UEFI.

I might also look at SSD tools from SSD vendor and see what that shows or lets you change.

---

