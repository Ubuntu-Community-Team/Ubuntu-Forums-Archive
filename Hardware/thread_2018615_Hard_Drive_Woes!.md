---
title: "Hard Drive Woes!"
date: 2012-07-06
forum: Hardware
---

### Post by Slimmons on 2012-07-06
Hey all, I just wanted some opinions on my setup that i'm currently working on.  I have two WD caviar blacks(1tb), two WD caviar greens(a 1tb, and a 2tb)  I originally wanted to set the two caviar blacks into a raid 0, for better performance read/write speed (because I've been using a green for two years now and i'm about to pull my hair out).  Since I know raid 0's are a bit risky, I was going to have the caviar green 2tb backup my 2tb of black raid 0.  I've been told it's a better idea to just get 4 wd blacks, and set up a different raid , 10 or something like that, that has faster speeds, and backup.  Any thoughts?  I really would rather just use the hard drives I have, but if there is going to be an issue later on using just raid 0 with nightly backup, I'd rather do it right the first time.

---

### Post by ahallubuntu on 2012-07-06
What is it you're doing with your system and why do you need the extra performance you think a RAID offers you?

Is your green drive an "advanced format" drive?  If so, is the partition aligned correctly on a 2048 byte boundary?  If not, you're going to have severe performance issues.  A green WD drive will never be as fast a black drive, but if aligned correctly it should have decent performance for typical applications.

---

### Post by stderr on 2012-07-07
First off, I'd benchmark your greens against your black to see what performance differences there are. What sort of requirements do you have? Sequential read? Random read/write? hdparm -t /dev/sdX can give you a crude indication of sequential read rates. For a better range of stats, there's fio and bonnie++ in the repos.

RAID 0 across your 1Ts will increase performance, but you're left completely exposed. I strongly advise against that, unless this is data you couldn't care less about. A RAID 1 can give you somewhat increased read performance, but you're left with a 1T total array size. A RAID 10 largely gives you the best of both worlds - but to use that you'd need another two 1T blacks. You want to keep the drives in the array as similar as possible; preferably identical.

Note that unless you have a (rather expensive) hardware RAID controller, the job of managing all these extra iops falls on your CPU - hence, you will take a hit on computational ability.

For us to best advise you, we'd need to know how much data you have, how you expect that to grow over time, the read/write requirements of the data, your CPU, the I/O controller(s) you have, and your budget.

---

