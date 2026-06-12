---
title: "HPLIP does't add Printer to cups"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by Romi on 2007-08-19
Hi,

i tried to install my printer on my server (-> no X, no windowmanager). I have a HP PSC 720 which is directly connected with USB. I'm using Feisty Fawn.
So, I downloaded HPLIP from its website and installed it (automatic install). I had to install cups manually, because the automatic installer popped out an error for that one.

Now, when I try to run hp-setup (Driver file for HP PSC 750, I think thats the correct one?), it asks it's questions and tries to add my printer queue to cups. The following error occurs:
```
Error: Printer queue setup failed. Please restart CUPS and try again.
```
I tried to restart cups -> same error.

Maybe someone can help?

Thank you so far,
Roman

---

### Post by nosrednaekim on 2007-08-19
You don't need HPLIP to set up a print server. What you do is go to "<your server's IP>:631" and that is the web-based set up for cups.

---

### Post by fyathyrio8 on 2007-08-19
Forgive me if I am wrong, but I believe HPLIP is supposed to install the drivers for the printer.  Also, is port 631 something you set in the conf file?  It doesn't work for me.

---

### Post by fyathyrio8 on 2007-08-19
OOOOOO.  HPLIP has an automated installer too.  I did not realize that, I have only dealt with the manual install.  I am tinkering now.  Will post any findings.

---

### Post by Romi on 2007-08-19
Thank you so far.

```
You don't need HPLIP to set up a print server. What you do is go to "<your server's IP>:631" and that is the web-based set up for cups.
```
The Webinterface is not acessible via Network. I can only access it on localhost.

> Will post any findings.
Thank you ;)

Two more things: 
It does not work with the HPLIP from the Reps, too!
I think I did something wrong with cups.. Will dig for a standart conf-file.

EDIT: Nope, config is okay.

---

### Post by fyathyrio8 on 2007-08-19
I successfully used HPLIP.  To do so, I first ran
[http://prdownloads.sourceforge.net/hplip/hplip-2.7.7.run](http://prdownloads.sourceforge.net/hplip/hplip-2.7.7.run)
after going through all the prompts, it makes you reboot.  After rebooting, I downloaded [http://prdownloads.sourceforge.net/hplip/hplip-2.7.7.tar.gz](http://prdownloads.sourceforge.net/hplip/hplip-2.7.7.tar.gz) and unpacked it.  Then, I opened that directory and ran setup.py .   I am sure there is an easier way to run the setup.py without having to download the second package, but rather than contemplate it, this is what I did.  Good luck!

---

### Post by Romi on 2007-08-19
> **fyathyrio8 said:**
> I successfully used HPLIP.  To do so, I first ran
[http://prdownloads.sourceforge.net/hplip/hplip-2.7.7.run](http://prdownloads.sourceforge.net/hplip/hplip-2.7.7.run)
after going through all the prompts, it makes you reboot.  After rebooting, I downloaded [http://prdownloads.sourceforge.net/hplip/hplip-2.7.7.tar.gz](http://prdownloads.sourceforge.net/hplip/hplip-2.7.7.tar.gz) and unpacked it.  Then, I opened that directory and ran setup.py .   I am sure there is an easier way to run the setup.py without having to download the second package, but rather than contemplate it, this is what I did.  Good luck!
Thanks for your Answer, but setup.py does exactly the same as hp-setup.

---

### Post by fyathyrio8 on 2007-08-20
Did you run hplip.2.7.7.run or whatever that file is prior to the setup?

---

### Post by Romi on 2007-08-21
Yes, I did run the installation. As said above, in automatic mode.

---

### Post by Romi on 2007-08-25
*bump*
Its still not working :(

---

