---
title: "permission issue in migrating from Windows"
date: 2005-12-04
forum: General Help
---

### Post by midol on 2005-12-04
Hi,

I recently persuaded a friend to try Ubuntu 5.04 after several years of increasing frustration with Windows. For the most part everything has gone well. But in a recent discussion it turns out she is unable to write modify her files from My Documents that I moved from W98 to a corresponding folder on her new desktop. Looking into it I saw that this is because I moved them as root then didn't give her write access after they were in place. I thought this would not be a problem, just chmod -R and the job would be done. But it seems that no matter what I do I can't get Ubuntu to work this way. Is there some problem I don't understand that makes me change permissions on all the files and folders one at a time?

Dave

also if there is a better forum for this please let me know.

---

### Post by tonderai on 2005-12-04
Did you do ...

sudo chown -R user.user /home/user/*
sudo chmod -R u+rwx /home/user/*

Otherwise, what does ls -l say?

---

