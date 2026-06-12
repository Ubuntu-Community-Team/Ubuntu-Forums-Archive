---
title: "Operating System Not Found?"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by Avaryan on 2006-01-09
I recently installed ubuntu on a server of mine and the installed phase appeared to go fine, but when it rebooted after initial installation I received the message "Operating System Not Found"...something like that.

I don't see why it's doing that, I believe I set everything up correctly.

My system was also running XP Pro.

Other info: Have a 120 GB IDE HD, 2 40 GB SSCI HD's, and 1 18 GB SSCI HD.

I'm trying to install Ubuntu on the 18 GB SCII, but it's not working.

Any advice or if you need more info then post it here.


Thanks

---

### Post by frodon on 2006-01-09
It's because the boot sector is not on the good parition i think, all you should have to do is to boot again on your install CD on go to the partition step then edit your linux partition by adding the boot sector. After that press the "escap" button and exit the install cd.

---

### Post by Avaryan on 2006-01-09
Might work, can you explain it alittle further? I want to be sure to do it right.

Edit: Just checked, it actually says, "Error loading operating system"....if that makes a difference. I suppose it's better than Operating System  not found.

Also, it gives me a list a kernals to install, which would be better..there were 3 of them.

Linux 386
Linux 386 - Image
2.6...something like that

---

### Post by frodon on 2006-01-09
it's a little bit different because i already got a "Operating System Not Found" message after a wrong install. But in your case, if i understand well, you didn't get any error messages during the install.
So if the system starts loading it's not a partition problem but an install problem.

If you can't anything like login using recovery mode you should try to run the install process again and see if you get the same problem.

---

### Post by Avaryan on 2006-01-09
I've ran the install so many times that I can do it with my eyes close.

The install goes error free, but when it says it's going to reboot, I get an "Error Loading Operating System" message.

I'm thinking about disconnecting all the HD's except for the one I'm installing to, then there shouldn't be anyways to make a mistake.

I'm thinking that's it's detecting the OS, but not finding it the MBR.

Edit: Just to say this...this has never began loading.

---

### Post by Avaryan on 2006-01-09
Well...still not sure what was wrong, I'm thinking it might have been a bad copy of Ubuntu.

I just installed Kubuntu and it seems to be working now.

---

