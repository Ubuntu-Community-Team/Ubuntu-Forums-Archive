---
title: "Tahoma Font not working in bold"
date: 2008-09-14
forum: General Help
---

### Post by awiggin on 2008-09-14
Hi all,

I downloaded the Tahoma font and moved it into my fonts folder, along with Tahoma bold.

I then refreshed/updated my cache with fc-cache -f -v .

I restarted the computer and now Tahoma works, except for one thing.  I can't get the bold to work.  When I use nautilus to look in the fonts folder, tahomabd.ttf is there.  It's just not recognized.

Any help?

Thanks,
awiggin

---

### Post by Pro-reason on 2008-09-14
Make sure that your font files are marked as readable by everyone.

---

### Post by awiggin on 2008-09-20
Hi.  Sorry about the delay on this.

How do I do that?

Part of the reason I want to be able to get Tahoma and Tahoma bold to work is because that is the only thing that seems to be stopping Mozilla Thunderbird email from working on my ubuntu set up.

And I really like Tbird email.  

Thanks.

Again - the problem is that I can't seem to get the Tahoma bold font to work.  I got Tahoma to work, but the bold isn't recognized.

-awiggin

---

### Post by Pro-reason on 2008-09-21
Use “cd” to go the directory where the fonts are.

Use “ls -l” to view the contents.  On the left is the notation indicating the permissions.  

You can make all the files in the directory be readable by everyone by typing “sudo chmod +w *”.

That will fix it if permissions are the problem.

---

