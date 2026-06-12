---
title: "Unlock Western Digital Hard Drive"
date: 2013-05-05
forum: Hardware
---

### Post by kiran1247 on 2013-05-05
Hi,

I've portable western digital hard drive which was "password" protected.
So, inorder to open the hard drive , first i need to unlock it , and then move further.

But I'm UNABLE to unlock it.

Can someone please help me and guide on how to unlock the hard drive after plugging the portable hard drive.

Thanks
Kiran

---

### Post by MartyBuntu on 2013-05-05
Ask the person who password protected the drive for the password.

---

### Post by steeldriver on 2013-05-05
Is this one of the hardware-encrypted 'Passport' drives? if so then afaik it's only possible to unlock it via Windows

I guess it *might* be possible to run the Unlock.exe (or the WD SmartTools app) via wine - however you'd need to get a copy, on Windows the drive mounts a virtual CD (VCD) with the unlocker on it

There are a few related hits if you google e.g.

[http://forum.winehq.org/viewtopic.php?t=12694](http://forum.winehq.org/viewtopic.php?t=12694)

---

### Post by kiran1247 on 2013-05-06
Thanks Steeldriver for the reply.

So there's NO way I can unlock it under linux directly?

Actually, I can unlock it under windows without any issues , but doesn't work under linux.

Can you help me here - Do i need to follow any procedure/steps in linux to unlock it ( install anything inorder to acheive this)?

thanks
kiran

---

### Post by Mark Phelps on 2013-05-06
With these WD drives, the encryption is done in hardware -- so of course, there is no software way around it.  If there was, the encryption process would be worthless!

You're also not really "unlocking" it when you access it via MS Windows; instead, you're only gaining read/write access.

What MIGHT work, because others have tried it, is seeing if there is an option in the Windows front-end to the drive to REMOVE the password.  That essentially decrypts it and it then should be accessible in Linux.

---

### Post by steeldriver on 2013-05-06
^^^ there is that option in Windows if you have installed the full WD SmartWare management / backup application (under 'Drive Settings')

---

### Post by kiran1247 on 2013-05-06
Actually I've a solution for this like - 
1. Unlock it via windows
2. Remove the password protection option
3. Login to Ubuntu
4. Plugin the drive , and this time drive doesn't ask me to unlock it though I've removed it already.

This would be fine , and works!

So, finally I guess we can't unlock it directly from UBuntu(linux) , am I right ?

Thanks
Kiran

---

### Post by steeldriver on 2013-05-06
I *doubt* you will be able to run the unlocker under wine - I tried it briefly (it just popped up a cryptic assertion error) but I'm not a regular wine user so I don't know all the tricks (I *think* it requires a big chunk of .NET 4.0 stuff)

If you have access to a windows box the instructions are here: [http://wdc.custhelp.com/app/answers/detail/search/1/a_id/3741](http://wdc.custhelp.com/app/answers/detail/search/1/a_id/3741)

---

