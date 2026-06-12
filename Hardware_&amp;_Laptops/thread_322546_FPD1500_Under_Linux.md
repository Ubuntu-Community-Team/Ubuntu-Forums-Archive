---
title: "FPD1500 Under Linux"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by mesapiegrande on 2006-12-20
Ever since Dapper Drake came out I have never been able to get my video working properly.

I have a GeForce TI4200 and a Gateway FPD1500 Monitor.  No matter what I do this combination does not work.

I found the following information at 

[http://groups.google.com/group/comp.os.linux.setup/browse_thread/thread/205342c8221c97/554a6194d9d112ee?lnk=st&q=Gateway+FPD1500+LCD+Monitor+--+how+to+make+it+work+under+Linux&rnum=1#554a6194d9d112ee](http://groups.google.com/group/comp.os.linux.setup/browse_thread/thread/205342c8221c97/554a6194d9d112ee?lnk=st&q=Gateway+FPD1500+LCD+Monitor+--+how+to+make+it+work+under+Linux&rnum=1#554a6194d9d112ee)

I will try it tonight and see what happens.

"I own one of these **LCD** monitors, and it is a -fabulous- **monitor**. 
 Unfortunately, XFree doesn't detect it properly. 
  After much research, and reading through many postings asking for 
 help, I discovered the answer in a comment made by a person named Kim 
 Khoon Chua. Unfortunately, the original posting is no longer available 
 on **Linux**.com, and Google does not have Kim's comment containing the 
 information -- just the original posting. 
 
 For the sake of those who love their FPD1500s, and want them to **work** 
 **under ****Linux**, I'm posting the details I remember here -- and of course 
 I'll send them to the KDE folks. 
 
 - - - - - 
 
 The key to getting your **Gateway ****FPD1500 ****LCD ****Monitor** to **work ****under** 
 **Linux** is this: the **FPD1500** does not correctly report information about 
 itself. In order to bypass this hardware flaw, you must do two things 
 in your XF86Config file: 
 
 1) Manually set the horizontal and vertical refresh rates, and 
 2) Set the "IgnoreEDID" flag to "on". 
 
 Essentially, you're telling X to ignore the information that the 
 **FPD1500** reports, and use your settings instead. 
 
 Here's an excerpt from my personal XF86Config-4 file: 
 
 Section "**Monitor**" 
         Identifier "**FPD1500**" 
         VendorName "**Gateway**" 
         ModelName "**FPD1500**" 
         HorizSync 30-61 
         VertRefresh 56-76 
         Option "IgnoreEDID" "on" 
         ModeLine "1024x768/60Hz" 65  1024 1048 1184 1344  768 771 777 806 
 -HSync -Vsync 
 EndSection 
 
 The HorizSync and VertRefresh lines define the manual settings, and 
 the Option "IgnoreEDID" "on" line disables use of the automatic 
 settings. Finally, the ModeLine entry contains all the nitty gritty. 
 Voila! 
 
 Here's a second excerpt, showing the "1024x768/60Hz" entries in the 
 "screen" section (I also have a regular CRT running at 100Hz, which is 
 why you'll see those entries in this excerpt): 
 
 Section "Screen" 
     Identifier  "Screen0" 
     Device      "Card0" 
     **Monitor**     "**FPD1500**" 
     DefaultDepth 24 
     Subsection "Display" 
         Depth       32 
         Modes "1024x768/100Hz" "1024x768/60Hz" "640x480" 
                 Virtual 0 0 
     EndSubsection 
     Subsection "Display" 
         Depth       24 
         Modes "1024x768/100Hz" "1024x768/60Hz" "640x480"     
                 Virtual 0 0 
     EndSubsection 
     Subsection "Display" 
         Depth       8 
         Modes "1024x768/100Hz" "1024x768/60Hz" "640x480" 
                 Virtual 0 0 
     EndSubsection 
     Subsection "Display" 
         Depth       16 
         Modes "1024x768/100Hz" "1024x768/60Hz" "640x480" 
                 Virtual 0 0 
     EndSubsection 
 EndSection 
 
 I sincerely hope this helps some folks out there. Many thanks to Kim 
 Khoon Chua for discovering this information, wherever you are (and 
 whoever you are). ;)"

---

### Post by ingo on 2006-12-22
Well, did it work for you? I doubt it since dapper uses xorg, not XFree. How about installing an NVidia driver, that might well take care of your monitor problem. Below is an excellent link for edgy:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by mesapiegrande on 2006-12-22
So I tried this to no avail.  I also followed TSELLIOT's guide and am still unsuccesful.  ](*,)

---

### Post by ingo on 2006-12-22
Sorry mate, don't know any further apart from googling your monitor and "linux". Another port of call might be the xorg forum...

---

