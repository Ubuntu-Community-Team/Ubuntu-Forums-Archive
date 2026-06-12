---
title: "Apache problem following upgrade to Hardy"
date: 2008-09-10
forum: General Help
---

### Post by sharong on 2008-09-10
I have a LAMP server which was running quite happily on Dapper.  Then I decided to upgrade to Hardy, and it seems to have broken something.

If I change the directory (in default, in the sites-available folder) to the general folder that I store all my websites in, and if I have a file called test.php in there (which displays phpinfo), then pointing to that file works fine.

Equally, I have a folder for a site that just uses fairly basic php - no re-routing of anything, just all in one directory - when I point to that in default and then go to localhost, it's fine.

But, I have a folder in which I have a php app, which has .htaccess files and various things - it is also used on Windows so it has a wee bit more in the way of config stuff, and is generally more complicated.  If I point to it, I just get a blank page.  Even if I put test.php in there, and try to view it, I still get a blank page.

This directory used to work fine - I haven't changed anything in it since the upgrade.

It looks like the server is somehow being rerouted away from the correct folder or something.  Is there any reason why this might happen?

Or does anyone have any other suggestions?

Thanks for the help!

---

### Post by sharong on 2008-09-10
Update - got this working.  It seems to be a php5 issue from when I upgraded.  Apache was looking for a directory called /usr/lib/php5/20051025, which no longer exists - the new version seems to be /usr/lib/php5/20060613+lfs.

I fixed it by making a directory called 20051025 and copying the contents of the other one into it - but that's probably a very bad way to do things!!

Anyway, once I restarted, it seems to be ok.

---

