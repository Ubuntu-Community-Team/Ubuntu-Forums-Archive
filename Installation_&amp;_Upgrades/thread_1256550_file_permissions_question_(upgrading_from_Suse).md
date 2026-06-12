---
title: "file permissions question (upgrading from Suse)"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by rockhoppe7 on 2009-09-02
Hi,
I'm running Suse 10.3 with my /home directory on a separate partition.
I want to switch to Ubuntu Jaunty - but I'm worried about the file permissions of my data - because the Ubuntu installation will consider that my data files were created by a different user, will I have problems with permissions when I restore the data back to my new system?  What should I do to avoid these problems?  Can I change the file permissions/ownership after I've restored the files?
Can anyone forsee any other problems I might run into with this?
Thanks.

---

### Post by syrag on 2009-12-29
Rockhoppe7, did you ever get any help on this? I'm bumping this because I'm in a similar situation.

Background: I am (was) a longtime user of Suse and when I bought my last PC I made it dual boot with Suse and Ubuntu. I would have gone entirely Ubuntu, but there were problems with Hardy and ATI drivers, so I stuck with suse as the main system and installed Hardy on a smaller partition.
I've since upgraded to Jaunty, and now Karmic, and I've had no problems at all, while my suse installation is continually giving me problems with new software (installing kdenlive broke miro. sheesh!) So now I'd like to go totally Ubuntu.
Here's the problem:
I have a suse /home partition, and Ubuntu won't recognize this on installation.* Also, my /home partition is too big to copy and restore. Can I just boot into my current Ubuntu and 'chown username.username' for the users I have on the suse /home partition , and then do an installation?
Any thoughts are appreciated.

*Why is this? Is there a good historical reason that one linux distribution can't or won't recognize a home partition from another? I know that Ubuntu isn't the only distribution like this, so this is not a slam at Ubuntu, but rather an earnest question.

---

