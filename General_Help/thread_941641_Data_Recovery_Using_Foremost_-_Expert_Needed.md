---
title: "Data Recovery Using Foremost - Expert Needed"
date: 2008-10-08
forum: General Help
---

### Post by appzattak on 2008-10-08
Hey all, I recently ran Fslint to do a little house keeping on my 8.04 laptop and it deleted some stuff I needed. So I decided to run Foremost to get most of it back since a lot of what was deleted was docs and pictures. Before I did this I had about 8.5GB of free disk space on my sda3 partition. So I ran this command= sudo foremost image.dd /dev/sda3 -o /home/steve/recovered

And I let it run for a bit, I noticed that it had created a bunch of folder in that recovered directory so I was checking if it had found anything, but it had not. However, all the while this thing is running I see my disk space is decreasing pretty fast....after about 20 mins I was down to 900MB, so I stopped it. I looked in that folder and there was only 10MB of foudn files, so I deleted the whole directory as root, yet my free disk space was still 900MB. So I ran Disk Analyzer to see where it all was, well I cannot for the life of me see where the heck all that free space went.

Can anyone tell me what I could do here to get my free space back. 


--Steve

---

### Post by appzattak on 2008-10-15
anyone?

---

### Post by special_user on 2009-03-23
Just delete that recovered folder you created.

ALso if you want to see something inside the folders created in the folder "recovered" you need to give permissions

chmod 777 -R /path/to/recovered/folder

hope it helps

---

