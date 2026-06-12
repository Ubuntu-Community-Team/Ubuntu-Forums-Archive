---
title: "HP 7310 Officejet driver?"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by pwrcul on 2009-06-01
I installed 9.04 and am linked over ethernet through a router to an HP 7310Xi Officejet AIO (printer, scanner, copier, fax) and want to use the driver that supports it for printing, scanning, etc.  

I first went through the Admin -> Printer setup and chose 7300 driver.  It works for printing but there is no control over ink coverage, etc.

I then went to Synaptic and installed hpoj and hpoj-xopanel which I guess are not included by default, but Synaptic also uninstalled hplip & hpjis.  hp-ppd also is not now installed.

I ran Admin -> Printer setup and was offered the same 7300 choice as before after I deleted the previous 7300 driver.  So I restarted (old windows habit) and now while running Admin -> printer I am offered a series of Officejet choices but none for 7310, e.g., I am offered Officejets 6110, 7110, 7130, 7140, 9100.

Should I reinstall hplip?  What do you suggest?

---

### Post by lindsay7 on 2009-06-01
Try installing HPLIP from  synatics that should work for most HP printers. It should give you all the functions, print, scan.  You should also install XSANE which is the scanning software (also in synapic).

---

### Post by pwrcul on 2009-06-01
Thanks to Lindsay7 for the suggestions.

I went to Synaptic and requested the hplip and found Xsane is already installed.

Synaptic will uninstall hpoj and hpoj-xopanel if I install hplip (it will also reinstall hpjis).

So it seems the Synaptic developers think you should use one or the other.  I can live with that, but then I am not sure what driver to use with the Officejets?  Which ones give me the greater ability to manage the AIO device?

At this point I will wait to see what others think.  I did not reinstall hplip.

---

### Post by lindsay7 on 2009-06-01
I just set up and Hp office jet 3680. It uses HPLIP which covers newer printers, copies, fax. My 3680 is an all in one. When you go to System/administration/printing. All you do is select new. It should find your printer and that is about it. Mine was ready to go after that and the menu from HPLIP has a gui that includes prining, copy, scan, and fax, but I so not have any fax software installed and do not need any as I can do that from the hp all in one from the phone key pad.  I would install HPLIP and plug in the printer and see if you have it as easy as I did.

---

### Post by pwrcul on 2009-06-01
Thanks again Lindsay7.

Before I followed the suggested advice to return to Hplip, I thought I would run the Admin -> Printer wizard again with the Hpoj alternative to see what it first offers as a driver selection.

When I clicked the Forward button this time it highlighted the Officejet 7140 driver so I chose it and ran a test page.  I got what looks to me to be an exact duplicate of the 7300 test page I got earlier through the Hplip option.

However, the driver seems to give me no greater control of ink usage:  No draft reduced ink, etc., much less than the Windows driver does.  

Is there a way to get that level of printer control in Ubuntu?

---

### Post by lindsay7 on 2009-06-01
I hate to be repetitious, but it is all there in HPLIP.

---

### Post by lindsay7 on 2009-06-01
Take a look,

[ATTACH]116099[/ATTACH]

---

### Post by lindsay7 on 2009-06-01
and,

[ATTACH]116100[/ATTACH]

---

### Post by pwrcul on 2009-06-01
Yet, again, thanks.

I discarded 7140, used Synaptic to get the same 6 hp packages in your screenshot in 8 above, but I don't find the HP Device Manager shown in 7 above.  How do you open it?

(Meanwhile, I had tried Xsane under the OJ 7140 driver and got an error message "v4l:/dev/video0" invalid option, but once Hp OJ 7300 was reinstalled I found a fax option and Xsane manager works.)

---

### Post by pwrcul on 2009-06-01
I found the HPLIP Toolbox under Preferences.

---

### Post by lindsay7 on 2009-06-01
When you go to printing and click new, it should find your printer and set up. When ever you go to print something you will get his screen. or you get it by clicking on the icon which should install on your top menu bar if you have one.

---

### Post by pwrcul on 2009-06-01
Lindsay7, thanks again, esp. for the screenshots and your patience.

Getting used to the HP Linux interface vs Windows was a key part of what tripped me up.  Now I have the defaults the way I like them, etc.

---

### Post by lindsay7 on 2009-06-01
Hay great, I know it is hard to believe that setting up the printer could be so easy in Ubuntu. I installed the printer in windows with the hp setup disk and it took about 10 minutes and it wanted to install a bunch of extra junk for window, like live chat and other stuff.

Enjoy your new system!

---

