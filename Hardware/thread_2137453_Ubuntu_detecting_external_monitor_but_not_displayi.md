---
title: "Ubuntu detecting external monitor but not displaying with vga/hdmi converte"
date: 2013-04-20
forum: Hardware
---

### Post by kathreen on 2013-04-20
I have Ubuntu 12.04 LTS installed on my old Dell Laptop D620, and I hope to just have it connect to my Philips tv monitor (4-8 years old) and work as a way to get internet easily on my tv. The laptop has vga out and the monitor only had hdmi in. So far I have tried two different vga to hdmi converters ([       Etekcity Video VGA to HDMI 1080P Converter/Adapter  ]("http://www.amazon.com/gp/product/B008COJXHC/ref=oh_details_o01_s01_i01?ie=UTF8&psc=1")and currently [       Sewell Hammerhead VGA to HDMI Converter, 1080p . ]("http://www.amazon.com/gp/product/B006LP0FXA/ref=oh_details_o00_s00_i00?ie=UTF8&psc=1") Whenever I connect the converter, I can see the display in my monitor section but when I try to output I just get a blank screen. I've tried playing with the resolution, but no change there resolves this problem. The vga port works fine, I have hooked it up successfully on another monitor using a vga cable. I have another newer computer with Windows 7 that is experiencing this same problem (detecting but not displaying.) I know my hdmi cable works because I use it regularly to connect to this computer to the same tv (the computers' vga also works fine.) I had this same problem with my last converter, but I returned it thinking it is a bad one (also what the manufacturer thought).

I know this might not be Ubuntus fault but I'm not really sure where else to turn. I've tried googling a bit for this problem, without too much luck. I'm also curious if anyone has  had similar issues or success using a vga to hdmi converter.

---

### Post by Duhruh on 2013-04-21
I've seen this before and remember reading on some obscure forum it was because of the type of monitor I was using, I would take that with a big grain of salt, it may be a long shot but try running 
 
xrandr --auto

in the terminal  while you have the cables connected.

---

### Post by kathreen on 2013-04-21
I tried xrandr --auto and I'm still having the same problem. The laptop in displays only has the external monitor, when I click the button to send the image out to the external it comes back to the laptop pretty fast (like it tries and fails to display to it so it comes back to the laptop.) Anyways thanks for the idea.

---

