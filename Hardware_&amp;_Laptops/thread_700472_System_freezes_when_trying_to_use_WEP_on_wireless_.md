---
title: "System freezes when trying to use WEP on wireless network. My solution, sortof."
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by wrongdave on 2008-02-18
I'm not asking for help here, just noting what I did in case someone else runs into the same problem.  I'm just a casual Linux user and my solution was actually to just get a different wireless card, but here are the details of what got me to that point (may save someone else some time)

When I installed Ubuntu 7.10 on my laptop and tried to connect to my home network using WEP encription, the system would freeze forcing me to do a hard boot. 

So after rebooting, I started into my 1st noob mistake. I figured I needed to experiment with the network settings so I proceded to manually set up the connection. I don't recall the actual settings I employed but they didn't work and the system froze again. 

I once again rebooted, and now linux would not complete the boot process (sorry, but I forgot the error it gave). After a couple more attempts, I decided to reinstall the operating system. (Just a side note here, I later read some other threads that led me to believe that if I would have removed the network card before rebooting, the system may have booted up ok, but I have no way of knowing that now since I reinstalled the system). Pretty sure my problem here was related to me manually setting up my wireless connection.  
So now my system is reinstalled, and to play it save, I make a backup image of the partition before going forward. I try the wireless connection again, and it freezes again. 

Before going any further, I started searching the web for solutions. I found the same problem (not necessarily with the same card) mentioned in several places, but did not find one with the solution. I did, however, find this thread [http://ubuntuforums.org/showthread.php?t=603154&referrerid=495487  ]("http://ubuntuforums.org/showthread.php?t=603154&referrerid=495487")that helped me out a little. It pretty much told me not to screw with the manual settings, and to try connecting through the live CD instead of the installed operating system. 

So I booted from the live CD and tried connecting with the same results (system freezes and I needed to force a reboot). 

Next, I turned off the WEP on my network, rebooted into the Live CD, and was surprised to see my wireless connection working fine. 

Now I turned WEP back on, rebooted, and tried connecting again being real careful with all the WEP settings (make sure you select Hex if that is what you are using). And again, the system freezes. 
Not really knowing what to do at this point, I decided to boot into the operating system (not the live CD) with a hard-wired connection to my network and download all the updates available, then try connecting with my wireless card. So after downloading all updates (and making another backup image), I rebooted into the system and tried setting up my connection again with WEP, and again the system Freezes. 

So now I figure that it is either my card, the drivers for my card, something stupid I'm doing with the settings, or the linux kernel itself that is having a problem with WEP. I had already invested many hours on this and figured I would next just try the easiest solution (for me at least), which was to just get another card and try that. Plus, it was time I upgraded to WPA anyway, so I ordered a new card and router. 

My original card was a D-Link DWL-650, and I ordered a new D-Link DWL-650G for 20 bucks. I knew it was risky getting a similar model, but my other card was at least 5 years old and I doubted they still used the same chipset. 

I get my new card, and even though I would be switching to WPA and using a new router, I 1st tried the new card using WEP on my existing router, just to satisfy my curiosity. Well, everything worked fine. I then set up my new router, and switched to WPA, and it also worked fine. 

So in conclusion, I'm thinking the problem was probably in the driver for my original card. For those of you with more linux skills that me, you can possibly find a solution for this, But for me, 20 bucks for a new card was well worth it. Obviously, I spent more than that since I also got a new router, but that's unrelated to the problem other than it gave me an excuse to upgrade to WPA.  

I'm happy now.
Hope this is helpful to others with this problem.

---

