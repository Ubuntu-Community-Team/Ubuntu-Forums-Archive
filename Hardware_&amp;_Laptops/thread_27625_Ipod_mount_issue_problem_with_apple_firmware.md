---
title: "Ipod mount issue: problem with apple firmware?"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by mtron on 2005-04-17
Hi! 

So i had nothing really interresting to do over the weekend, and wanted to go into the  Ipod via Firewire mounting issue. I switched from warty to hoary about a week ago. 

My Ipod is a 3rd gen model with the latest apple firmware on it. 

Running on warty i had no problems connecting it via firewire. Now on hoary ( i did a complete reinstall, not an upgrade) the ipod was not recognized, nor mounted. dmsg did not display an error. No workaround I found in the forum helped for me. 

I compared the version numbers of the kernel, hal, volume manager ect. from hoary with the last debian sarge testing packages and found some differences, so i installed beside ubuntu sarge main (not testing), spend some time with configuring and tried to connect. No success. 

Ok. changed sarge sources to testing, updated and. wow! it worked! the Ipod flashed "Do not disconnect", so I mounted it manually and tested it. Everything fine. I wrote down the lately updated packages with the version numbers and booted into hoary. 

Now it is getting weird. 

I did not even started checking the packages and connected the Ipod and.... what the s**t... it mounted without a problem and worked. 

So. now i am really confused. I refused to believe it. disconnected the ipod, restarted the box, and again. it worked. 

after I once got it working it is now working all the time. That can't be the reason of the OS'es in my case, or why should it work on debian, and afterwards also in ubuntu? (debian is installed on my second harddisk) 

So i think it must have something to do with the apple firmware on the Ipod, or what do you guys think about this?

---

### Post by TravisNewman on 2005-04-18
doesn't sound like it'd be the OS, you're right-- though it could have been that Ubuntu was having a "burp" and  something had gotten mixed up. That's happened to me before with my Nomad.

---

