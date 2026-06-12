---
title: "Mass, repackaged deployment"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by Arador Aristata on 2009-01-05
Our company has been spending a lot of money on MS products for years on end now and I was recently approached by our MD to look into alternatives for our Users. After an assesment of the products we use and a good bit of Testing on my work machine I want to upgrade one of our sites to Ubuntu and run it as a test environment before upgrading the rest of the company.

I will run the PC's with dual boot in case we hit any major snags but the goal is to migrate our entire company to Ubuntu on the desktop and later start looking at the servers.

Now after playing around and installing all packages I feel would be needed I am looking for a way to repackage everything I have on my machine into a bootable CD for the rest of the people in the company. We have identical Lenovo M55e's all across the company due to our recent upgrade but I hardly feel like going through all these packages again for the 70 users on the test site.

Is there a way to make a bootable CD/DVD out of an installation that will include all the packages?

Thank you

---

### Post by ajgreeny on 2009-01-05
Have a look at remastersys which could be just what you want.  I've never used it nor had reason to do so, but it looks interesting.
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by compman25 on 2009-01-05
Can you do a net install from an internal ftp server with your own iso?

---

### Post by maybeway36 on 2009-01-05
If you want a net install, you should probably look at Ubuntu's text-based installer, almost (but not exactly) identical to the one used in Debian. You'd have to mirror the packages to an APT repository on your server and preseed the installer (to point it to your server and tell it what packages to install), but it can probably be done.

---

### Post by Arador Aristata on 2009-01-06
Thank you very much. Will have a look into Remastersys. I was looking at creating a disc image but only had MS SMS to work with and couldn't get it to work properly. Will look into some other tools as well.

---

