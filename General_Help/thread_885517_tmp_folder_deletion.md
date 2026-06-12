---
title: "tmp folder deletion"
date: 2008-08-10
forum: General Help
---

### Post by madhatter563 on 2008-08-10
I am using the program "Motion" to take snapshots of a security camera when motion occurs and then uploading it to an ftp server.  I have the files saving in the tmp folder..

I want it in a temp folder so that the files will be deleted fairly often (because just walking by the camera creates roughly 10 pictures).  However, I believe that the tmp folder is only deleted when the machine reboots.  Well, since this is a server I would rather it stay on versus some sort of scheduled reboot.  Is there any way to clear the folder every hour or so?  Can I do it without making a script?  Thanks for any help in advance!

Oh by the way.. I'm using Ubuntu 8.04 Desktop Edition (could not use server edition because of some kernel issue at boot).

---

### Post by damoxc on 2008-08-10
The way I would do it would be to stick a script in /etc/cron.hourly.
Script doesn't have to be very clever at all, simple
```
rm /tmp/*
``` would do the trick.

---

### Post by Keith Hedger on 2008-08-10
this is not a good idea as ```
rm /tmp/*
``` will remove all the files in /tmp that it can other programs may need these file u should be a bit more specific ie:```
rm /tmp/jpeg/folder/*.jpg 
``` i dont know if the pics are placed into a seperate folder or not but it wont take a lot of experiment to find out the correct command to use.

---

### Post by Elfy on 2008-08-10
Perhaps it might be better if you could set up a different folder and set the script to run there

---

### Post by madhatter563 on 2008-08-10
Thanks for all the ideas!  I took a mix of all the suggestions.  While searching how to format the script correctly I found a way to add it to the "crontab".  So here is the script i ended up making and adding to crontab.  I used this simple generator to format it correctly:
[http://www.htmlbasix.com/crontab.shtml](http://www.htmlbasix.com/crontab.shtml)

0 * * * * rm /home/user1/security/*.jpg >> /home/user1/security/logs

So, if all works correctly.. it should delete all jpgs in the security folder on the first minute of every hour (which of course runs every day/month/year).  I also had it save logs to the same folder so that I can see if it ran correctly every hour.. though I'm not sure if I will keep it.  It hasn't gone past the first hour yet so I'm just waiting for it to run.  Hopefully it works :)   Thanks again for all the help!

---

### Post by madhatter563 on 2008-08-10
Looks like it worked just fine.  The logs file is just a blank document named logs.. but Im not too concerned about that.  All files had uploaded to my FTP server then deleted out of the specified folder at the beginning of the new hour.  Now I don't have to worry about getting 14k images in the folder at once!

---

