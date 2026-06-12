---
title: "'no punp backends found' and 'cannot login to database' in Mythbuntu Setup"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by mulluysavage on 2009-02-25
I've followed the Mythbuntu troubleshooting guide on this, but can't complete some of the steps. 

sudo mysql - root mysql
returns a list of values so I think that mysql is running.

I see in the terminal that shows while I'm trying to run MythTV Setup "access denied 'mythtv'@'localhost'. I follow the troubleshooting steps for this in the troubleshooting guide, and successfully added 'mythtv' as a user to the mythtv group, but then cannot remove ~/.mythtv and /home/mythtv/.mythtv as the guide specifies: "access denied."

I've also tried the steps described in troubleshooting "access denied 'root'@'localhost' since I've seen this error too. Here, the troubleshooting guide says to check my password with mysql -u root mysql and enter it. I am denied access and not asked for a password.

I have also seen in the forums that the problem may be solved by specifying 127.0.0.1 instead of localhost, which I have tried wherever mythtvsetup asks for server name, but this has not worked either.

It seems like some kind of simple permissions problem to me, but it's a little too tangled for me at the moment. Can anyone help?

Thanks!

---

### Post by mulluysavage on 2009-02-28
After searches, I see that a few people have had this problem. I don't have to build my system from the ground up again, starting with a clean Mythbuntu install, do I?

---

