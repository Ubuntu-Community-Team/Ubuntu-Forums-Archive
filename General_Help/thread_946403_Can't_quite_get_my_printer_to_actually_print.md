---
title: "Can't quite get my printer to actually print"
date: 2008-10-13
forum: General Help
---

### Post by Dr.Suave on 2008-10-13
I've just bought an HP Deskjet D1460 - I've installed HPLIP and the HPLIP-GUI. I've tried using it with both the recommended drivers. But when I click print, the printer jumps into action, starts chugging and all that business, sucks the paper up, and then does nothing. Nothing at all, except flash the 'something's wrong' light at me. The HP Status Service and Document Print Service both tell me the print job is being processed, but I suspect otherwise... after waiting for a bit I have to pull the paper out myself, and turn the printer off at the wall.

Now, admittedly, I am using paper from a notebook, which is quite thin (it is a straight edge though), but I don't think that's the problem.

One website I've found ([http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Deskjet_D1460](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Deskjet_D1460)) suggests I assign the printer as a Deskjet D1300 - I have no idea how to do this.

Can someone help?

Wilf

---

### Post by dburnett77 on 2008-10-13
I don't have an HP printer, but the HPLIP site had the following info. for installation:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

and here's the troubleshooting section:

[http://hplipopensource.com/node/224](http://hplipopensource.com/node/224)

---

### Post by Dr.Suave on 2008-10-13
Yeah, I followed the instructions exactly when I installed the printer - and I've checked the troubleshooting - nothing there that seems to apply...

Not really sure why this isn't working - I'm on 7.10 with USB 1.0 if that's any help.

Wilf

---

### Post by -Zeus- on 2008-10-13
have you tried real paper?  you might want to

---

### Post by Dr.Suave on 2008-10-13
I have now, and I get the same problem.

---

### Post by Dr.Suave on 2008-10-13
Ok, got it working - was pretty simple in the end - one of the drivers thought the printer had no paper and was refusing to print - after a restart it started working.

Does anyone know where the PPD files are kept in Ubuntu? I can't print directly from GIMP before I tell it where to look.

---

### Post by dburnett77 on 2008-10-13
In the Places menu, "Search for Files..." and the old convention of:
*.ppd

will yield the files and their locations.

---

