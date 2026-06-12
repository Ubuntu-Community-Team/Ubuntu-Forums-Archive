---
title: "HP Deskjet D2560"
date: 2008-08-28
forum: Hardware
---

### Post by leveliv on 2008-08-28
okay, I need this printer to work...Ubuntu recognizes it...as the d2560 but there's no driver? :S 

When I try to print a test page...it seems like it's going to work but the power light just sits there and blinks so I know the computer is at least talking to the printer..

Is there a generic driver I can use?

---

### Post by silkstone on 2008-08-28
Do you have hplip installed (you can get it with Synaptic - it's in the repos).

This may also help...

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by joris.vh on 2008-09-28
You have to uninstall hplip because the actual version (in Ubuntu) is not maked for the D2560 (I have got the same printer). After, you'll have to download it on [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html). Run sh hplip-xxx.run (where xxx is naturally the file's version) and follow the instructions. Good luck.

PS: I'm sorry for my bad English, I'm Belgian...(if you've got time, you can say me where are my mistakes ; )

---

### Post by gwad44 on 2008-09-28
Thanks for your help. However, just in case anyone else finds this as well....I found that the hplip-2.8.8.44.run file on HPLIP website didn't open with sh. However if you go into SourceForge.net and search for hplip theres a .tar.gz version (a newer version as well). Just download that extract it and click on the hplip-install file. It should all run as expected in terminal from there. 
Cheers

---

### Post by jezzabart on 2008-09-29
Thank you very much for this help, especially Gwad44 who posted just 18 hours before I had the same problem whilst trying to install a printer that I had just advised my friend to buy because I was certain it was supported, having checked the HP web-site.  Very embarrassing.

A further note is that, in my case (Acer Aspire M1204, AMD Athlon 64 bit, Ubuntu Hardy Heron) I followed Gwad44's instructions and successfully printed a test page with a picture of assorted fruit.  I then rebooted the computer and the problem was the same as before - the printer light flashed and the job never finished.

I went into the printer configuration dialogue and deleted the old version, but still no luck.  Eventually, I unplugged the printer, deleted all relevant entries in the printer list, rebooted the PC, connected the printer and ran [FONT="Courier New"]sudo hp-setup[/FONT].  After this, a test page was produced with Ubuntu printed on it, the Ubuntu logo and a set of colour gradients and the printer still works on subsequent restarts.

Thank you all again.

---

### Post by JC Denton on 2009-04-13
> **gwad44 said:**
> Thanks for your help. However, just in case anyone else finds this as well....I found that the hplip-2.8.8.44.run file on HPLIP website didn't open with sh. However if you go into SourceForge.net and search for hplip theres a .tar.gz version (a newer version as well). Just download that extract it and click on the hplip-install file. It should all run as expected in terminal from there. 
Cheers

Thanks for sharing this with us. My experience is similar to that of others here. My problems with installing this printer were solved when I installed the tar.gz version post installing hplip using synaptic.

---

