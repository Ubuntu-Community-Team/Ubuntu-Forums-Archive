---
title: "Another Scrren Resolution Problem"
date: 2009-10-03
forum: Hardware
---

### Post by Levy1234 on 2009-10-03
Hi folks.  I have noticed a number of people have similar problems to mine, but I am still not clear on the solution.  I have a dell latitude E5400 laptop and an intel mobil 4 series adaptor.  This is a fresh install of Jaunty on a new computer that has never had linux before.   The problem is that while I sometimes get the proper screen resolution of 1280 x 800, I usually get a lower resolution, 800 x 600.  I have tried several things.  First, this problem seems most common with nvidia, but I do not have nvidia.  Second, I looked under hardware drivers, and there was no relevant driver.  Third, I tried typing "  sudo dpkg-reconfigure -phigh xserver-xorg" but it did not help.  A number of folk in other posts mentioned editing xorg.conf.  I looked at mind and there is virtually nothing there.  This is all there is exceot for the commented out stuff

  	 	 	 	 	 	  Section "Device" 
 	Identifier	"Configured Video Device" 
 EndSection 
  
 Section "Monitor" 
 	Identifier	"Configured Monitor" 
 EndSection 
  
 Section "Screen" 
 	Identifier	"Default Screen" 
 	Monitor		"Configured Monitor"    	 	 	 	 	 	  Section "Device" 
 	Identifier	"Configured Video Device" 
 EndSection 
  
 Section "Monitor" 
 	Identifier	"Configured Monitor" 
 EndSection 
  
 Section "Screen" 
 	Identifier	"Default Screen" 
 	Monitor		"Configured Monitor" 
 	Device		"Configured Video Device" 
 EndSection
 
 	Device		"Configured Video Device" 
 EndSection



I do not know anything about this file, but it seems to me that if it were the problem, I would never get the proper screen resolution.  But I have noticed that several people have posted the contents of their xorg.conf files and they were filled with stuff!  I have no idea why mine is so empty.  



This is my work computer and our tech person (who often uses Ubuntu himself) did not have a clue, beyond that it probably had something to do with xorg.  He suggested waiting until the next verson of Ubuntu comes out to see whether the problem is solved, but I am hoping to figure out what is going on.  

Any help is much appreciated.

---

### Post by Levy1234 on 2009-10-06
I did not get a reply but was able to find the solution.  Ubuntu seems to have trouble with many graphics cards include intel.  I followed some leads and ended up on this page

http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html?fbc_channel=1#{%22id%22%3A0%2C%22sc%22%3A%22http%3A%2F%2Fwww.facebook.com%2Fxd_receiver_v0.4.php%22%2C%22sf%22%3A%22loginStatus%22%2C%22sr%22%3A2%2C%22h%22%3A%22loginServer%22%2C%22sid%22%3A%220.202%22%2C%22t%22%3A0}[0%2C%22loginStatus%22%2C%22InitLogin%22%2C{%22session%22%3Anull%2C%22settings%22%3A{%22feedStorySettings%22%3Anull%2C%22inFacebook%22%3Afalse%2C%22locale%22%3A%22en_US%22}%2C%22connectState%22%3A2%2C%22baseDomain%22%3A%22%22%2C%22publicSessionData%22%3Anull}%2Cfalse]

That is one hell of an URL!  Anyway it is about a repository for video drivers that have not yet been put in the main repository.  The site said it could take months to get them out.  It is the xorg-edgers repository.  So I added them, updated, and things now seem to be working.  

So the problem seems solved.  (I do not seem to see a button to mark the thread solved.)

---

