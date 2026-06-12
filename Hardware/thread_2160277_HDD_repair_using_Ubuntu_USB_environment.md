---
title: "HDD repair using Ubuntu USB environment"
date: 2013-07-06
forum: Hardware
---

### Post by ipant on 2013-07-06
Hello all. First post here, hopefully somebody will be able to help..

I have a compaq 610 laptop with a dual boot configuration (Ubuntu + win7). Last night my HDD (NTFS) probably crashed and I cannot boot to any of them. If I choose win7 after a lot of waiting it goes to the HP repair utility which at the end it goes for a restore to the factory settings which I believe erases all the data in the HDD.
If I choose Ubuntu after a lot of waiting it goes at an environment with commands (initfram or something), and I am totally lost how to use that.
I have tried to enter safe mode using the F8 key, no luck.

I thought of using a usb Ubuntu environment in order to be able to see the HDD, recover the necessary data and then it can go for a format. 
The USB did work, I see the drive but I cannot mount it (not sure what that is) or open it. Also for some reason, the USB environment cannot connect to the internet using the wifi.  

More or less that's the story. I was wondering if there is an application or tool to use with the Ubuntu stick and recover the data from the drive. Or if there is another idea that I haven't think of, please guys let me know.

Thanks in advance..

---

### Post by Mark Phelps on 2013-07-06
If the windows filesystem gets corrupted, Linux will not let you mount it -- in order to prevent further damage.

Unfortunately, there is no Linux equivalent of the Windows CHKDSK -- which is used to scan and repair Windows filesystems.

If you can remove this drive and connect it to another Windows PC, you might be able to run CHKDSK on it that way.  Otherwise, the only option you would have would be do recovery folders and files using a Windows data recovery app.

---

### Post by ipant on 2013-07-07
> **Mark Phelps said:**
> If the windows filesystem gets corrupted, Linux will not let you mount it -- in order to prevent further damage.

Unfortunately, there is no Linux equivalent of the Windows CHKDSK -- which is used to scan and repair Windows filesystems.

If you can remove this drive and connect it to another Windows PC, you might be able to run CHKDSK on it that way.  Otherwise, the only option you would have would be do recovery folders and files using a Windows data recovery app.

Mark thank you very much for the response.
I'll try using Hirens probably and then see what else I can do.

---

