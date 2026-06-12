---
title: "[SOLVED] test page from a printer crashes (samba)"
date: 2008-08-01
forum: General Help
---

### Post by lil_elvis2000 on 2008-08-01
Hey all,
  I have a Samsung laser which is setup on my Ubuntu machine using cups. it work brillinatly and my other Linux machines can print directly to it. brilliant.
  I then followed the Samba HOW To to setup the printer and printer drivers. using the printer with Windows drivers which I have loaded from the CD on works great.
  BUT when I try to install the drivers to the SAMBA [print$] share via the process which is documented in the HOW TO (to get point'n print to work)..and then I use the Test Page button on the printer properties..it crashes. And not just the dialog, the status bar, etc.. all goes away. Luckily it restarts.

  I have managed through the rpcclient to set the printer driver to '' (which gives an error but works, a bug?). And then remove the driver from the tdb using deldriver, and then delete the files.
  I then re-add the printer in windows and load drivers from the CD and it works.

  Any ideas what it going on. Some type of corruption I am guessing when the files are uploaded/downloaded. The printer properties also came up fine, but I don't think it worked...permissions perhaps?

  Thanks for any help..

I think for now I'll pass a CD round the office to install the drivers.

---

### Post by lil_elvis2000 on 2008-08-04
Apparently, before I can touch anything...before I can print. I need to save the printer settings into SAMBA's tdb files for each printer.Otherwise...crash!

Can't try it out - not without uninstalling drivers from at least one machine - so I'll just say that this is not a problem. 'twas my fault for not RTFM.

Would be handy if somehow (maybe in SAMBA 4.0) this could happen automatically when drivers are loaded?

---

