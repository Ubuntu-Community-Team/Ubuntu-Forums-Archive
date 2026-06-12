---
title: "Phenom II X3 720 BE unlocked fourth core FYI"
date: 2009-10-07
forum: Hardware
---

### Post by djchandler on 2009-10-07
[SIZE=2]My Phenom II X3 720 (Heka core, 2.8 GHZ) Black Edition is now running with all 4 cores in Ubuntu. I just bought it and the motherboard and RAM on Sunday 04/10/09, but did not do the swap until Tuesday, 06/10/09 (d/m/y). Some of the older steppings of this processor may not allow this procedure. My CPU has a product  number (OPN) of HDZ720WFGIBOX. The serial number should begin with a 9. It *is* Socket **AM3**.

I got my X3 720 at Micro Center in Overland Park, KS for $117.99 (US). When you consider a a stock [/SIZE] [SIZE=2][COLOR=Black][Phenom II X4 945 Deneb]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103696")[/COLOR][/SIZE][SIZE=2][COLOR=Black] running at  3.0 Ghz sells for [/COLOR]$169.99 today (07/10/09) and the [/SIZE][SIZE=2][Phenom II X3 720]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103649")[/SIZE][SIZE=2] sells for $119.00, this is a bit of a bargain with just a least bit of effort on your part. This core will be recognized asa Deneb when unlocked. Also remember this is a Black Edition. Going to a multiplier of 15 is child's play for this CPU. The 945's multiplier is locked. And the 720 requires only 95 watts too.
To be fair, they have a [/SIZE][SIZE=2][Phenom II X4 940 Deneb 3.0GHz Socket AM2+ 125W Quad-Core Black Edition ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103471")[/SIZE][SIZE=2]for $169.99 too. If you can't use an AM3 CPU, this looks pretty good too. But check what your motherboard will do first in terms of offering overclocking option first.

Get specs on the Phenom II X3 720 here:

[http://products.amd.com/en-US/DesktopCPUDetail.aspx?id=522](http://products.amd.com/en-US/DesktopCPUDetail.aspx?id=522)

[http://www.cpu-world.com/CPUs/K10/AMD-Phenom%20II%20X3%20720%20Black%20Edition%20-%20HDZ720WFK3DGI%20(HDZ720WFGIBOX).html]("http://www.cpu-world.com/CPUs/K10/AMD-Phenom%20II%20X3%20720%20Black%20Edition%20-%20HDZ720WFK3DGI%20%28HDZ720WFGIBOX%29.html")

You don't need software for this if you get the right motherboard/bios combination.

My motherboard is a Gigabyte MA785GM-US2H. It has a dual bios built in. It also allows you to image the bios to disk (make sure you have an NTFS or FAT32 partition) so you can easily undo this if problems arise.

[http://www.gigabyte.us/Products/Motherboard/Products_Overview.aspx?ProductID=3143](http://www.gigabyte.us/Products/Motherboard/Products_Overview.aspx?ProductID=3143)

This was swapped on an existing Ubuntu install (9.04) and was okay eventually. Had network problems due to changed MAC address on the onboard ethernet adapter that resolved after resetting router and ethernet switch. You might get around this by switching the  location where the CAT5 cable plugs into your ethernet switch.

Here's what you do.

Restart your computer and enter the BIOS. Look for a setting called **Advanced Clock Calibration**. My board uses an Award BIOS and I found it in the **MB Intelligent Tweaker (M.I.T.)** menus. It so happens it is the first item selectable in the **M.I.T.**

Open **Advanced Clock Calibration**. There you will find the two pertinent options, **EC Firmware Selection** and **Advanced Clock Calibration** again. To enable the fourth core, change **EC Firmware Selection** to *Hybrid* (*normal* is default) and **Advanced Clock Calibration** needs to be set to *All Cores* (*disabled* is default).

That's all there is to it. Back out by pressing *esc* until you get back to the **Main Menu**. Select **Save & Exit Setup**, answer **Y** to save your changes and the system will reboot.

After rebooting and logging into Ubuntu, open System Monitor. Here's what my screenshots look like after doing this.

Disclaimer: YMMV  menu.
:guitar:
[/SIZE]

---

