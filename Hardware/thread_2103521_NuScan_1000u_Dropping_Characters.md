---
title: "NuScan 1000u Dropping Characters"
date: 2013-01-10
forum: Hardware
---

### Post by cignature on 2013-01-10
I have been reading around these forums, and other places on the Internet.  Including this [similar thread]("http://ubuntuforums.org/showthread.php?t=1112575"), And I cannot seem to find a solution to my problem.

My bar code scanner will drop specific characters on specific bar codes, on Linux only (works fine on Win XP).

I have 3 codes to work with at the moment, (there are other problem codes).

Correct -> Returns
0125589**8** -> 0125589
01258**2**62 -> 0125862
0125441**4** -> 0125441

I have attempted:

[LIST]
[*]usbkbd and usbhid separately.
[LIST]
[*]They both suffer the same issue.
[/LIST]
 
[*]Inter-Character Delay
[LIST]
[*]Attempted: none, 10msec, 20msec, 50msec.  No Effect.
[/LIST]
 
[*]Message/Block Mode.  No Effect.
[/LIST]
I have also attempted packet sniffing the USB port, and while I got output, I was not able to interpret the results.

**On Screen Output: **
0125589

**Sniffed Data:**
edcad200 57874715 C Ii:6:002:1 0:8 8 = 0000271e 1f220000
edcad200 57874839 S Ii:6:002:1 -115:8 8 <
edcad200 57882671 C Ii:6:002:1 0:8 8 = 00000000 00000000
edcad200 57882779 S Ii:6:002:1 -115:8 8 <
edcad200 57890657 C Ii:6:002:1 0:8 8 = 00002225 26250000
edcad200 57890734 S Ii:6:002:1 -115:8 8 <
edcad200 57898653 C Ii:6:002:1 0:8 8 = 00000000 00000000
edcad200 57898700 S Ii:6:002:1 -115:8 8 <
edcad200 57906640 C Ii:6:002:1 0:8 8 = 00002800 00000000
edcad200 57906690 S Ii:6:002:1 -115:8 8 <
edcad200 57914631 C Ii:6:002:1 0:8 8 = 00000000 00000000
edcad200 57914682 S Ii:6:002:1 -115:8 8 <

Does anyone have a suggestion on where I can go from here?

---

