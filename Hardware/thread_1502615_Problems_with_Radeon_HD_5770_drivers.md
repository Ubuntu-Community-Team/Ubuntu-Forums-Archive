---
title: "Problems with Radeon HD 5770 drivers"
date: 2010-06-05
forum: Hardware
---

### Post by cronin4392 on 2010-06-05
I just installed 10.04 and was trying to install video drivers mainly because I have dual monitors. Before installing drivers messed around with the Monitor settings and could sometimes get both monitors but it would always mess up once i log out. I checked the AMD website and saw they had drivers so I installed those. After logging out I was able to set up dual monitors but the highest resolution was 1440x900 and my main monitor is 1650x1080. I installed and reinstalled the drivers two different ways the AMD site said, one way specific for 10.04 but could not get them to work without problems. I followed the instructions here:[http://ubuntuforums.org/showthread.php?t=697982](http://ubuntuforums.org/showthread.php?t=697982) and now on restarts it reverts back to default settings which is just on my smaller monitor. When I open the AMD control panel it says that there are problems because either there are no drivers or i need to configure with aticonfig which i already did. Whats the best thing to do and are there better drivers for AMD cards? Any help appreciated.

---

### Post by SeePU on 2010-06-05
> **cronin4392 said:**
> I just installed 10.04 and was trying to install video drivers mainly because I have dual monitors. Whats the best thing to do and are there better drivers for AMD cards? Any help appreciated.
I'm interested in the 5770 cards since I want to upgrade mine.

I follow the Phoronix website since there's a lot of discussion on these drivers and the cards. 

You went to this page?:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

You'll want Catalyst 10.5 Proprietary Driver

Then follow these instructions:

Uninstall the old driver first as explained in the instructions.

This page might help, too.  I would check it out.  

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

### Post by cronin4392 on 2010-06-06
> **SeePU said:**
> I'm interested in the 5770 cards since I want to upgrade mine.

I follow the Phoronix website since there's a lot of discussion on these drivers and the cards. 

You went to this page?:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

You'll want Catalyst 10.5 Proprietary Driver

Then follow these instructions:

Uninstall the old driver first as explained in the instructions.

This page might help, too.  I would check it out.  

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Thats the driver I downloaded and Ive already tried those instructions.

---

### Post by SeePU on 2010-06-08
> **cronin4392 said:**
> Thats the driver I downloaded and Ive already tried those instructions.Okay, sorry it didn't work for you.

I just read that you have to turn on vsync and use OpenGL for watching video but Compiz/Effects have to be off.  If it's still not working, then I don't know what's wrong.

---

### Post by cronin4392 on 2010-06-09
> **SeePU said:**
> Okay, sorry it didn't work for you.

I just read that you have to turn on vsync and use OpenGL for watching video but Compiz/Effects have to be off.  If it's still not working, then I don't know what's wrong.

I guess i could try that but that wasnt my problem. I just needed to install my video driver so i could use the capabilities of my video card and have dual monitors.

---

### Post by SeePU on 2010-06-16
Fglrx driver ver. (Catalyst) 10.6 is out now... Does that help at all?

---

