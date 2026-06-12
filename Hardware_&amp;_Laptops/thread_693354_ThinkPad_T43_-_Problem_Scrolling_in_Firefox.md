---
title: "ThinkPad T43 - Problem Scrolling in Firefox"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by Palumbo on 2008-02-10
I recently installed Ubuntu 7.10 on my ThinkPad T43. 

Ubuntu immediately recognized both the trackpad and track button. It did not recognize the center button used for scrolling up and down in long documents. 

I followed the instructions I found on [ThinkWiki :: Scrolling ]("http://thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Scrolling") to configure the center button. I got it working, but now I have a new problem. When scrolling through a long web page in Firefox, the browser will send me "forwards" or "backwards" through my previous web pages. 

I've only experienced this in Firefox. I'm sure in large part because everything else I've scrolled through doesn't have a "forward" or "back" button associated with it. 

Has anybody else experienced problems like this? 

Any information you could provide would be greatly appreciated. 

Thanks, 
Palumbo

---

### Post by Palumbo on 2008-02-14
Alright, I think I've solved my own problem...sort of. 

I was having some minor issues with enabling extra and advanced visual effects. I soon got tired of the eye candy and wanted the windows to move and react like I'm used it. Once I turned off all of the compiz type effects, Firefox began to behave. 

Now I can scroll up and down long web pages without being sent back and forth through history. 

Since I'm still a Linux novice, I don't know the relationship between these aspects of the OS's functionality. I hope to understand why one would affect the other. 

-Palumbo

---

### Post by Palumbo on 2008-02-14
Now that I think about it, there is another possible reason for the fix. 

When I was following the tutorial from [Think Wiki]("http://thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Scrolling"), it instructed me to add the following lines to the xorg.conf file: 

Option                "YAxisMapping"            "4 5"
Option                "XAxisMapping"            "6 7"

Last night I took out these two lines from xorg.conf, but didn't notice anything different. This morning (and more importantly after a reboot), the problem is no longer an issue. This might have also been the fix I was looking for as well. 

-Palumbo

---

