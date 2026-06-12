---
title: "newbie question......."
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by chaosky on 2007-03-13
hi all, im a new player in UBUNTU. Right now im using UBUNTU 6.10 on my notebook..
i got a few questions to ask, hope u all can help me.
1. when i opened device manager many of my hardware didnt recognize by UBUNTU,where i can get my notebook driver for ubuntu, im using BENQ 5200G
2.i cant use my wireless correctly.......
3.when i installed the KWifi Manager, ubuntu is become not responding....!!!
4.i cant connect to my network print server. my print sever is Dlink & my printer is SAMSUNG ML-1610.....

thx
for advanced..:) 

Chaosky

---

### Post by chaosky on 2007-03-14
:popcorn:

---

### Post by bikeboy on 2007-03-14
1. Most drivers are made by the Linux community and are built into Ubuntu rather than being provided by the hardware manufacturers. We're only lucky enough to get manufacturer backed drivers on a few occasions from nice companies.

2. Try searching the forums for your particular model of wireless card. If you don't find a solution, start a thread for it. "Newbie question" won't help others find the solutions if they have the same problems as you.

3. I can't help.

4. What model of Dlink print server is it? You might find other people have found how to get it working and have posted something on the forums about it. Also, can you get the printer to work if you connect it directly to your computer? (assuming that's possible to do)

---

### Post by gsparky2004 on 2007-03-25
Chaosky,

I'm also using a DLink print server (a DP311U) connected to an HP Photosmart P1000.  You may be going wireless, whereas I'm using a wired connection.  Still, here's what I did to get my connection working.

*  Open your web browser and type in "http://localhost:631" into your address box.
*  Click on the "Add Printer" button.
*  On the "Add New Printer" page, enter the following information:
  - Name: <name for your printer, BUT DON'T USE ANY SPACES!  For example, mine is simply "HP1000">
  - Location:  Doesn't matter.  Leave blank, if you want.  Or enter the location of Jimmy Hoffa's body, for that matter.  Yer choice.
  - Description:  Doesn't matter.  I entered the full name of my printer, which is "Photosmart P1000".
*  Click "Continue"
*  You should now see a box marked "Device".  It's a drop-down menu.  Since I'm using a DLink print server, I chose "LPD/LPR Host or Printer".  You may have a different device.
*  Click "Continue"
*  You should see a box named "Device URI".  Again, if you're using a DLink 311U (as I am), type in "socket://<DLink IP address>.  For example, the IP address of my DLink is 192.168.100.55.  So, I typed in "socket://192.168.100.55".
*  Click "Continue"
*  You now need to enter the manufacturer of your printer.  I scrolled down and selected "HP".
*  Click "Continue"
*  Yet another page that might trip you up.  You need to select the particular model of your printer.  The problem is that there are several models of "HP Photosmart P1000" listed.  I selected the "HP Photosmart P1000 Foomatic/hpijs (recommended) (en)".  There seems to be one that is "recommended" for each model.  I suggest going with that for the first try.  If it doesn't work, you will have to try others.
*  Click "Add Printer"
*  If everything works, you should see a message such as, "HP1000 successfully added!"

You should see a tab along the top of the page that says, "Printer".  Select that, then look for a button "Print Test Page".  If you press that button and get a proper print-out, you're set!

Hope this helps!

Gary

---

