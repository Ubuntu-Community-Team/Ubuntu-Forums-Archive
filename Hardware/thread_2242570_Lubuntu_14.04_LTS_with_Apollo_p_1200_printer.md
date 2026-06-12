---
title: "Lubuntu 14.04 LTS with Apollo p 1200 printer"
date: 2014-09-02
forum: Hardware
---

### Post by q123q on 2014-09-02
Hi All,

I would like to ask you guys for help:
my printer does not work.The new task is appears in the printing queue, but its gone after half a second.The printer is recognised by the Lubuntu.It is in the printers list.

Op system: Lubuntu 14.04 LTS  32bit
Printer: Apollo P 1200


Thank you All


Frank

---

### Post by scottrob12 on 2014-09-03
Hi
I used to have this printer and found that I could get it to work using the ppd file.
First of all remove the printer from system settings. I don't use Lubuntu but will assume you would locate it in system settings, right click and delete it from the computer.
Go to [https://www.openprinting.org/printer/Apollo/Apollo-P-1200](https://www.openprinting.org/printer/Apollo/Apollo-P-1200) and download the pcl3 driver by clicking on ' directy download ppd '. You should find it in your Downloads file in your Home directory if you are using Firefox ( and haven't changed it )
I would then use the browser to install the ppd vis CUPS.
Open a tab in the browser at [http://localhost:631/admin](http://localhost:631/admin)
Click 'Add Printer'
A List of Printers is displayed which should include the Apollo p1200. Mark it and click continue.
The printer should be displayed on the next 'Add Printer' page so check it and click continue
On the next page, the Apollo p1200 should be highlighted. At the bottom, select browse and select the ppd file. Select add printer. The printer should then install and you can then do a bit of maintenace via your browser.
If at any stage you are asked for a username/password, use your normal username. If that fails try root as username with your password.
Hope this helps though I must admit that it's over 8 years since I had that Apollo printer.
Bob

---

### Post by q123q on 2014-09-04
Hi Bob,

thank you for your great help. I did manage to fix it. I using it with non color ink, and windows also recongines as a color ink,and did not work if you not change it to "monochrome". Now it's works perfect. Thank you !

Frank

PS: If you around Somerset, UK  and need some help to fix your bicycle, just let me know.

---

### Post by q123q on 2015-03-19
Thank you Bob for your help, the printer is still works. I just want to give a little advice to other users: if you using a non color ink, set the printer to 
"Not Color-Managed" othervise it will refuse to work.(ink symbol keeps flashing) 
Cheers

---

