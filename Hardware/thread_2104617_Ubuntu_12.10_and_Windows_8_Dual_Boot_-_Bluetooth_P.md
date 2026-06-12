---
title: "Ubuntu 12.10 and Windows 8 Dual Boot - Bluetooth Pairing"
date: 2013-01-13
forum: Hardware
---

### Post by Aergan on 2013-01-13
I have a Dell L702X which has been enabled for UEFI via Custom BIOS and I have Windows 8 Pro x64 and Ubuntu 12.10 x64 successfully dual booting on GPT.
 
I have named my device under Ubuntu with the same visible name under Windows. All devices pair ok under each respective operating system but the pairs are unique and not shared between the two.
 
I am struggling to find a way to copy in my bluetooth peripheral keys from Windows 8 into Ubuntu 12.10. I can extract the keys from [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTHPORT\Parameters\Keys] from Windows but I can't find the "linkkeys" file that is supposedly under /var/lib/blueooth/[deviceid]/ ?
 
I am guessing the keys are now in a different place or a different method of access (if at all possible)?
 
Any help would be greatly appreciated.

---

### Post by rykel on 2013-02-11
I am using dual boot between Ubuntu 12.10 and Windows 7 on a 64-bit ASUS EeePC 1215B AMD Brazos system.

Likewise, I would like to simply copy over the "link keys" for both my Bluetooth Keyboard and Bluetooth Mouse instead of pairing them all over again each time I switch OS.

Please advise?

---

### Post by Tom Digicon on 2013-03-28
[http://ubuntuforums.org/showthread.php?t=1479056](http://ubuntuforums.org/showthread.php?t=1479056)
As to this post, the key is in Keys folder but the format does not look like a file called linkkeys but a string of numbers which are the keys.
Unfortunately, I do not have the chance to see it on my PC as I cannot find BTHPORT folder in Services (I use PSTools).
I use Windows XP. There are several detailed posts on this dualboot topic but all of them gives the same path with this folder.
I still search for it.
Tom

---

