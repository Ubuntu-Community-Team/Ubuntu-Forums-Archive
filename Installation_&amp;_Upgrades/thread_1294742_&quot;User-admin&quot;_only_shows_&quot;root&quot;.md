---
title: "&quot;User-admin&quot; only shows &quot;root&quot; after 9.10 Beta upgrade"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by lyricalpapa on 2009-10-18
After upgrading from Ubuntu 9.04 to the Ubuntu 9.10 Beta, my User-Admin utility now only lists "root" in the users and groups.

My username and group doesn't show. Neither do any of the other users and groups, including the Virtualbox group.

No usernames show in the login screen now, but I can still login by entering my name and password.

Virtualbox is still working for me.

When I log into Nautilus as admin "sudo nautilus" I get the following message:

> ** (nautilus:4991): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I've been remounting my "/home" partition intact when upgrading for the last several upgrades. Could there be a problem with the "/home" partition that is causing this? I've only been upgrading/reformating the "/" partition.

I've tried to file a bug report, but there appears to be a problem with the Launchpad server.

BTW, the Ubuntu 9.10 Beta runs much faster than 9.04 on my machine,

---

### Post by eznet on 2009-10-18
Same thing here.  users-admin doesn't show everything... Unlike yours, mine is showing my user and groups with both my root and user groups - just not any of my other many groups or users.

I noticed this when installing Virtualbox as well.

In experimenting, loading 'sudo users-admin' from CLI doesn't yield any error messages - I can edit just as I can after authorizing from the GUI.  Going the 'su UserName' results in "not having permission to make changes".

---

### Post by lyricalpapa on 2009-10-18
I lost my entries in the User-Admin in stages. 

My username and most of the groups disappeared when I first upgraded to 9.10 Beta.

Then all the usernames and all the groups, except "root" disappeared after I ran an update of the beta.

I burned an install disk of the beta and did a fresh install while keeping my original /home partition. My username and root showed up in User-Admin as both users and groups until I rebooted. Then my username disappeared completely.

I still have rights, but User-Admin is not showing me or any of the other usernames or groups except root.

Does anyone know if there is a way to re-establish the accounts so they can be seen with User-Admin? I'm flying blind now.

Is username and group account information held on the /home partition? Should I wipe a directory or my entire /home partition and start with a completely fresh install?

---

### Post by Popoi on 2009-10-30
Same problem here in final release. I just can't see root user, not mine. And in GDM my user is not listed, anyway I can push enter and login username and password.

---

### Post by postlude on 2009-10-30
Yes, I have the same problem with the 9.10 final release. It seems that the user that was logged in when the upgrade took place is removed from the Users and Groups list and therefore from GDM.

---

### Post by gstool on 2009-10-30
I have a similar situation, but think it may be due to my UID and GID being lower than 1000.  I have them set to 500 so I can share data partitions seamlessly with Fedora partitions where 500 was always the number issued for the first user.  I have been using 500 forever in Ubuntu, and my name would appear in the GDM login, but no longer.  It does not appear in the Users Settings list either, and unlike previously, there now seems to be no way to show all users.  Does anyone know how to get the list to show all users?  As others report, I can login by providing my username and password.  Where does one set which users appear in the GDM list?

Gerry

---

### Post by wersdaluv on 2009-11-01
> **gstool said:**
> I have a similar situation, but think it may be due to my UID and GID being lower than 1000.  I have them set to 500 so I can share data partitions seamlessly with Fedora partitions where 500 was always the number issued for the first user.  I have been using 500 forever in Ubuntu, and my name would appear in the GDM login, but no longer.  It does not appear in the Users Settings list either, and unlike previously, there now seems to be no way to show all users.  Does anyone know how to get the list to show all users?  As others report, I can login by providing my username and password.  Where does one set which users appear in the GDM list?

Gerry
Exactly the same case here

---

### Post by slochewie on 2009-11-03
Ditto here. All of our users UIDs and GIDs are between 500 and 800 at the moment. So they don't show up in the user-admin window. Conversely it is nice they don't show up in the dumb User List when they log in. 

Of course I'm not using the Beta but the Final Release....

---

### Post by barretr on 2009-12-15
+1.

---

### Post by jonmartin on 2009-12-28
The same happens here, 9.10 amd64 clean install. When running users-admin as root, only root shows, when running as my own user, all users are showing, but even though my user is allowed to administer, the authentication fails when I push the unlock-button.

Frustrating and lame. It has been working at some point, and I have no idea what have caused it to break.

---

### Post by A1Dox on 2010-02-28
I found this thread whilst trying to debug an issue I was having with timekpr-gui.py. I'd tracked the problem down to a problem where the python code parsed the values for UID_MIN/MAX from /etc/login.defs. 

The regex code populated a list with the min and max UID's, and the python error suggested the list wasn't being populated properly. So I fired up user-admin to see what UID values the accounts had, and found only the root user listed. I checked the values of UID_MIN/MAX in login.defs, and found the file was empty! In order to fix the python problem, I added the UID lines from the login.defs file on another machine, and, as well as fixing the python error, it made all the other user accounts re-appear in user-admin..!

I don't know how the login.defs file came to be empty, but it seems that, in my case at least, the user-admin problem was related to the missing values in the defs file. I guess, that user-admin must also work out what UIDs to list from those values. I've now copied the whole login.defs file from the other box,so will see if it stays populated or if something causes an empty file to be written into its place at some point.

I did find a post that suggested that login.defs was being depreciated and the content would be moving to other files, but all my Ubuntu machines are the same version, so I can't believe it really has been depreciated, and shouldn't have been empty on my problem machine.

As always, YMMV, but I hope this helps somebody suffering from the user-admin problem.

Regards,
Dox.

---

### Post by em3raldxiii on 2010-05-07
It appears that something during the update (or some other action) has broken the program that creates entries in your /etc/login.defs file.  The Users & Groups application checks this file for the minimum and maximum User ID numbers and then displays accordingly.

The values in mine were set to min and max being 0, which of course is why I could not see any users in my list.  It seems a popular minimum number is 999, and a popular max is anywhere from 2000 to 60000.  I set mine to be min 999 and max 1200.  After saving this file and re-opening Users and Groups, all my users show up again.

Here is a link to the existing bug report (and where I pulled my final answer from):  [http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg374791.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg374791.html)

So in summary:

1.  Close your Users & Groups program.
2.  Open a terminal (Applications > Accessories > Terminal)
3.  Type:  gksu gedit /etc/login.defs
4.  Enter your sudo password.
5.  The file should have two entries only, UID_MIN 0 and UID_MAX 0.  I changed both numbers to 999 and 1200 respectively.
6.  Save the file and close gedit.
7.  Open System > Admin > Users & Groups.  You should now see all your users.

According to the bug report, this problem should not occur in Lucid, therefor it's been marked "Triaged".

Hope that helps!!

---

