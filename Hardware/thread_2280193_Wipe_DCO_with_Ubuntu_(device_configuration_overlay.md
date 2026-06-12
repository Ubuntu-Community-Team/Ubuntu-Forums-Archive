---
title: "Wipe DCO with Ubuntu? (device configuration overlay)"
date: 2015-05-28
forum: Hardware
---

### Post by ian83 on 2015-05-28
The DCO on this Windows 7 computer is locked, and the virus I have is implanted in the DCO, as there is no HPA (host protected area) on this computer according to OSforensics, though that could be the virus blocking access to the HPA. Don't ask me how I know that there is a virus, just know that is in the locked DCO or HPA if there is in fact an HPA. I attempted to use Blancco 5 as it is purported to bypass the lock on the DCO and HPA, but the virus is blocking access to the Blancco servers so the product can't even register for a single wipe. I looked at HDparm but couldn't find a definitive answer on wiping a locked DCO/HPA. Please advise.

---

### Post by NoWayWin8 on 2015-05-28
I'd love to hear why you believe there's a virus in your DCO lol
 what's  the output of
```
# hdparm --dco-identify /dev/sda
```
vs
```
# hdparm -I  /dev/sda
``` ?

Wiping the DCO/HPA would render the drive unusable, so why not just do it the easy way with a hammer?

---

### Post by ian83 on 2015-05-28
Blancco support told me that using the full wipe of the drive would render windows 7 uninstallable, while other operating systems such as Ubuntu (I asked specifically Ubuntu) would still install. Please confirm/deny and I'll relay your response to Blancco.

---

### Post by NoWayWin8 on 2015-05-28
hdparm will do it for you.

WARNING This will erase everything and possibly render the HDD unusable.
```
# hdparm --yes-i-know-what-i-am-doing --dco-restore /dev/sda
```

---

### Post by ian83 on 2015-05-28
And Ubuntu will continue to work?

---

### Post by NoWayWin8 on 2015-05-28
It will remove all data from the disk and, if the HDD is not ruined you will have to reinstall.

---

### Post by ian83 on 2015-05-29
Pretty certain the virus is on the network, so whenever i wipe the drive with DBAN and reinstall windows 7 it just comes back. The most obvious things i have found the virus has disabled is full system restore (deleted recovery manager entirely and the dlls required to run it) and it blocks devices from being mounted in command prompt. If i go ahead with doing a full Ubuntu install ill likely choose lubuntu because the live boot of full ubuntu is extremely slow on my 4gb ram i5 pc, and i read of people having speed issues with 8gb ram and i7. Lubuntu live usb boot seems to run very smooth.

---

### Post by NoWayWin8 on 2015-06-01
> **ian83 said:**
> Pretty certain the virus is on the network, so whenever i wipe the drive with DBAN and reinstall windows 7 it just comes back. The most obvious things i have found the virus has disabled is full system restore (deleted recovery manager entirely and the dlls required to run it)

Wiping the drive with DBAN destroys the recovery or OEM utility partitions. You would have to contact the PC manufacturer for info on restoring those features after a drive wipe. Its very unlikely you have a virus.

---

### Post by ian83 on 2015-06-01
Completely untrue, DBAN doesn't remove the DCO and HPA which are the "recovery or OEM utility partitions" So you can very easily reinstall any operating system you wish, I've run the dban autonuke twice already. Dban is available to the public specifically because reinstalling windows is a snap, and because it doesnt wipe the dco and hpa it does not meet governmental data sanitization standards, which require every last bit of the drive to be wiped, which would require you to contact the manufacturer to get those sections reinstalled. I most definitely have a virus but I'll live with it because it is no longer monitoring my microphone Since the last time I wiped it.

---

### Post by NoWayWin8 on 2015-06-02
> **ian83 said:**
> DBAN doesn't remove the DCO and HPA which are the "recovery or OEM utility partitions".

No that's not correct. Recovery/OEM partitions aren't visible from within Windows because they have an attribute that tells Windows to not show them in the UI. They reside on normal addressable disk sectors and nothing protects or hides them from utilities like DBAN or other OS's.

---

### Post by ian83 on 2015-06-02
I dont believe that is correct, Blancco was created in order to bypass the freeze lock on the DCO and wipe the HPA in addition. If you were correct then I wouldnt have been able to reinstall windows immediately, twice i might add.

[http://superuser.com/questions/642637/harddrive-wipe-out-hidden-areas-like-hpa-and-dco-also-after-malware-infectio](http://superuser.com/questions/642637/harddrive-wipe-out-hidden-areas-like-hpa-and-dco-also-after-malware-infectio) This person back up my claim that DCO and HPA are not wiped by DBAN, therefore there hard drive was not 100% clean
"Malware in windows (yes), possibly rootkit/bootkit. Don't want to take  any chances. So, wiped drive with DBAN foolishly (PRNG, 8 pass). Later  came to know that DBAN does not kill HPA (host protected area) and DCO  (Drive configuration overlay) which are "hidden areas" (if present) in a  hard drive. Saw that HDDErase made by CMRR can remove DCO and HPA, if  present. But project was stopped in 2005 or 7. So, I came to HDPARM of  linux in the hope that it will wipe my HDD 100% clean so that i can **install crappy windows again on a 100% clean hard drive**. As an aside, I also looked at "BC Wipe Total Wipeout" which does HPA and DCO removal @ $50"

 And right from DBAN themselves (advertising blancco, which does in fact wipe DCO and HPA.)
[http://www.dban.org/node/35](http://www.dban.org/node/35)
"there are other [erasure solutions]("http://www.blancco.com/en/products/total-data-erasure/blancco-5/") that have the capability to detect, report and overwrite locked and hidden sectors such as HPA, DCO, and remapped sectors."
"Wiping the HPA would surprise and strand people that expect the HPA  to have rescue materials, and it often results in OEM technical support  marking and abandoning people that do it. The HPA is a low risk because  it is not accessible during normal operations. DBAN defaults are chosen to best protect people with a minimal  understanding of this kind of problem. This point is still open for  discussion in the help forum and in the appropriate bug ticket."

---

### Post by NoWayWin8 on 2015-06-03
We seem to be in agreement here: DBAN wipes everything but the HPA/DCO.

As far as whats on an HPA, a better source of information is your hard drive's product spec sheet which should be available on the manufacturer website (the HD manufacturer, not the computer manufacturer).

> If you were correct then I wouldnt have been able to reinstall windows immediately, twice i might add.

It would surprise me if you did the reinstallation without having to use an installation DVD or USB (...and the PC doesn't contain an internal mSATA drive or other separate memory device for recovery). Not saying it's not the case, but it would be unusual since every Windows PC I've seen had all the recovery partitions on the addressable sectors of the HDD and were only hidden from the Windows UI.

---

### Post by ian83 on 2015-06-03
> **NoWayWin8 said:**
> No that's not correct. Recovery/OEM partitions aren't visible from within Windows because they have an attribute that tells Windows to not show them in the UI. They reside on normal addressable disk sectors and nothing protects or hides them from utilities like DBAN or other OS's.

But in your more recent post you said we're in agreement that it doesn't wipe the dco or hpa, and yes I have the install disc for w7

---

### Post by NoWayWin8 on 2015-06-03
Recovery/OEM partitions != HPA/DCO

(they are NOT the same thing)

---

### Post by ian83 on 2015-06-03
> **NoWayWin8 said:**
> Recovery/OEM partitions != HPA/DCO

(they are NOT the same thing)
So then, how would I go about wiping the recovery/oem partitions?

---

### Post by NoWayWin8 on 2015-06-04
You already did with DBAN. They're all gone. This is why you have to use the DVD to reinstall windows. If the recovery partitions were still there the computer would be able to restore Windows without the DVD.

---

### Post by ian83 on 2015-06-04
Ah great, so i'll probably run dban again and fully install lubuntu because the virus has basically bricked w7 at this point, luckily I can still access my files even in w7, but the moment I try to open Firefox the whole thing freezes and I have to hold the power button to shutoff. Out of curiosity how can I find the size of the dco/hpa in lubuntu

---

### Post by ian83 on 2015-06-09
> **ian83 said:**
> Out of curiosity how can I find the size of the dco/hpa in lubuntu?

Sorry to bother you, do you have the answer to this question?

---

