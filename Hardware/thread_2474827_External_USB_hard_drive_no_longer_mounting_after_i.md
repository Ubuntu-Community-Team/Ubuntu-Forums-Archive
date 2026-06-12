---
title: "External USB hard drive no longer mounting after installing Windows 10 in parallel"
date: 2022-05-09
forum: Hardware
---

### Post by nickb486 on 2022-05-09
I recently installed back Windows on a separate internal drive and tried to open an external USB hard drive (which is set up as RAID 1). Windows read it as a RAW drive (Ubuntu sees it as NTFS) and I couldn't open it.
So I booted back into Ubuntu to copy out the data I wanted as I was just going to reformat it as NTFS once I had the data out onto my internal drive but now Ubuntu fails to mount it as well.
gparted doesn't see it which I guess makes sense since it's not mounted

blkid command shows it as type=ntfs

I had no issues with this drive when I first installed Ubuntu

What could be wrong here?
Thanks for any input.

---

### Post by yancek on 2022-05-09
A common reason for a Linux OS not to see or mount an ntfs partition is because it is hibernated.  Linux won't mount a hibernated windows partition and hibernation is the default on windows.  Check to see if it is off in your windows power settings.  If you turned it off previously, some windows updates will turn it back on and the user will not be notified.

---

### Post by nickb486 on 2022-05-09
So I went back and turned off the fast boot in Win10 as well as ran `powercfg /h off` in Powershell to turn off drive hibernation. 
This didn't work but strangely enough when I booted back into Windows the drive was available. 
Odd because I knew it was formatted as NTFS and not RAW to begin with so I'm not sure why Windows didn't recognize it. 
Regardless, I'll consider this resolved since I only plan to use this drive in Windows for now anyhow.
Thanks!

---

