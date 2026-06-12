---
title: "encryption problem on hard disk"
date: 2013-10-03
forum: Hardware
---

### Post by BeardedOne on 2013-10-03
After boot up:

1 -The hard disk encryption window came up, I entered the pwd, it was accepted, and I got the message that it was successful, the little clock icon timer spun - that's it. No desktop appeared.

2 - The second time I booted up, after entering the pwd, which was accepted and acknowledged as successful, the disk check program ran until it reached 98%. It stalled there.

3 - I went to the recovery window and selected a past/working version - same result as #1.

4 - I booted from a live-cd and tried to copy the home directory to an external drive. I didn't have permission.

5 - I went to root access from the recovery window, got to the home directory where access-private-files.desktop was and entered 'ecryptfs-mount-private' and the pwd. I got the message that the directory was 'not set up properly'.

This happened after I attempted to make an auto-login user ID, it wouldn't auto-login and I deleted the ID, keeping my admin ID intact.

I would like to get into the hard drive and copy the files to the external drive unencrypted.

Any suggestions?

Thanks for reading.

Bill

---

### Post by TheFu on 2013-10-04
When using encryption, having 100% perfect backups is critical. Seems you learned that now.
> I would like to get into the hard drive and copy the files to the external drive unencrypted.

Well, you encrypted the files for a reason ... to prevent _just anyone_ from being able to do exactly that, correct?

Did you make the key-file backup as suggested when creating the encrypted setup?  I just went through this yesterday after migrating from a 160G HDD to a 500G HDD on a laptop. It was pretty clear that I'd lose access to my HOME if I didn't.  I remember seeing that same screen during the install ... er ... last year.

So now I'll google a little ... "ubuntu encrypted home recovery" was the query - [http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/) was found plus lots of Ubuntu Forums [solved] pages were found. *sudo ecryptfs-recover-private* seems to be the magic phrase.

But the real lesson here is that when we encrypt, we intend to trade convenience for security. To me, that is fine. I'd rather have a little inconvenience than allow just anyone access to those files ... like when a laptop is stolen.  I say this after seeing 2 smartphones stolen on overseas trips within 2 days.

Good luck. Happy backups!

---

### Post by BeardedOne on 2013-10-04
Thanks for the link

---

### Post by BeardedOne on 2013-10-09
After 12 hrs of work, I fixed the problem. I'll write it here so someone else with these same symptoms won't have to work so hard. I spent a lot of time on the procedures listed in the link provided above and researched in other places, mostly working with ecryptfs, but that didn't work. It returned a variety of errors. It was a dead-end.

The key to the problem is statement #1 in the original post. The hard disk encryption was accepting my password and returning "successful". This means it wasn't an encryption problem. My hang up was past the encryption screen which meant it was a login problem. Further research began to show that encryption doesn't like autologin (I'll leave it to others to figure this out). Apparently, my attempt at creating an autologin user had broken something. Redefining the problem to a login hang up resulted in a different solution.

Solution:
1 - at the encryption screen, enter your usual password to decrypt the hard drive, look for it to return 'successfully decrypted...'
2 - while the screen appears hung, enter Ctl-Alt-F1 to start the terminal login
3 - at the prompt, enter your login
You've now gained control of your computer. Your files should be visible and can be copied.

Since I'm not that good at terminal commands, I found a way to restart the x system - 'pkill X'. That gave me complete control, mounted a USB drive and let me copy the files normally. I re-installed the OS and my files and was back to normal.

I hope this helps someone. It reminded me how important correct problem definition is to getting a good solution.

This is the spot where I usually thank all the people on the forum who have been so helpful. However, except for one remarkably condescending person, no one else replied. I'm not going to knock their contribution, at least they were trying to help.

---

