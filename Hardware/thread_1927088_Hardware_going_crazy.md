---
title: "Hardware going crazy"
date: 2012-02-17
forum: Hardware
---

### Post by Penguinion on 2012-02-17
Heya! I began having loads of problem mounting one of my 4 disks, where as one is installed with windows XP media center edition, one is installed with ubuntu 11.04 and the other two are for pure storage. For some reason there came up errors with one of my drives that there was an error code of 13. So i followed the instructions by typing "chkdsk/f" in windows and it seemed to work, a couple of days later it didn't work again.

So I went into windows to try this command again, and now it got stuck on the "Windows is starting up" screen. Pretty disturbing, so I thought something is way off with my windows, gotta have some sort of virus. So I decided to format and recover with my "Acer Recovery DVD" that formats and erases and then reinstalls windows. Now I can't even get past the dual boot >_<'.

After all this might sound like only windows problems, but after some research, it seems like my harddrive is not functioning correctly. As I go back to ubuntu, my general windows drive is mountable, but there comes up hundreds of spamming error pop ups saying this:

"Harddisk problems detected. A hard disk is reporting health problems." And then allows me to press Examine, Okay or Cancel.

I went to examine and got up this Disk Utility program. I enter the SMART data examination window, and look at the attributes where it says that the Spinup Retry Count test has failed. Also the Airflow Temperature.

The startup of the computer until dualboot section is awfully slow aswell. I'm thinking that something is way off here, never seen anything like it. Sorry for the gigantic amount of words in this long long story, but is my computer broken? Or my harddrive, or both?

Any answer appreciated, thanks.

---

### Post by Paddy Landau on 2012-02-18
I think your post answers it. The hard drive appears to be damaged.

You can try to use GParted to delete its partitions and recreate them (be sure to choose the correct drive or you'll lose your data!), and then reformat.

But the Smart Data has already told you that there's a problem, so I wouldn't expect it to work.

Sorry.

---

