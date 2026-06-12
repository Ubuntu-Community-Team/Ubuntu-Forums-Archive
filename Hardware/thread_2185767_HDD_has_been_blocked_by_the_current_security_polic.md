---
title: "HDD: has been blocked by the current security policy +No Bootable Device, Hit Any Key"
date: 2013-11-04
forum: Hardware
---

### Post by BSG Fan on 2013-11-04
My family gave me a new computer with Windows 8. But i do not like the new Windows, I always liked the 7 better than any else.
Since for the last 5 years I use Ubuntu 8 to 13.04, I wanted to reformat-erase the OS of that laptop Gateway in favor to the Ubuntu 12.04 and above.

My friend deleted its OS and he told me is ready for Ubuntu.

I installed (from CD-ROM) the 13.04 and it ended with success and asked me for a restart.
but...

the new system did not upload as was supposed to. Instead I have these windows in order:

[B]1. HDD: has been blocked by the current security policy
[ok][/B]

I hit ENTER and

[B]No Bootable Device, Hit any key
[ok][/B]

and

[B]Boot Manager
Boot Options Menu
1. HDD: ,WDC WD5000LPVZX-22VoTT0
^   |
|        to change option, ENTER to select an option[/B]

But, there are NOT other options to represent a List (as in any computer)

So, by conclusion, the installed Ubuntu 13.04 never uploads.

I really really need help in this one.
Thanks in advance

Note:
If my thread is not fix for this subforum, please move it to the one belongs.

---

### Post by TheFu on 2013-11-04
Start here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by BSG Fan on 2013-11-04
I am stuck.
The only I know thanks to the terminal doing this:
 [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

is that is:** EFI boot on HDD**

---

### Post by TheFu on 2013-11-04
Did you alter the BIOS settings as recommended in step 2 of the provided link?

---

