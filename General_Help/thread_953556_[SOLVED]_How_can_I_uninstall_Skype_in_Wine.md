---
title: "[SOLVED] How can I uninstall Skype in Wine"
date: 2008-10-20
forum: General Help
---

### Post by nyborjare on 2008-10-20
Well I thought I could get Skype running over Wine. No way....:confused:

Installed Wine 1.0 No problem there
Downloaded Skype 3.8 for Windows
(Have tried the Linux version with no luck)
Run it and some kind of installation started. But when trying to run Skype only a few flashing windows and nothing more..
OK
I want to get rid of the thing now but I cannot uninstall.
Have tried the uninstaller in wine but does not work

Can anybody help me in this.

Regards
michael

---

### Post by Sycron on 2008-10-20
I can't help you uninstalling skype but did you downloaded the linux version from here ? [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu) . I'm sure it works if you double click it.

---

### Post by Sam on 2008-10-20
If you don't mind about other programs installed in Wine you may remove the wine directory ~/.wine

---

### Post by nyborjare on 2008-10-20
Sam
Could you give me the commands for this action ??
I can accept to uninstall Wine for the time being

Michael

---

### Post by Sam on 2008-10-20
```
rm -r ~/.wine
```

---

### Post by nyborjare on 2008-10-20
Sam
Thank you for your support in this matter.
I followed your instructions.
While in terminal running your command I had to hit enter something like 8 - 10 times before I could interpet that the job was done. ????
Further more I had to manually take away wine from the aplications meny.

So right now all is gone and I seem to have  the state as before I installed Wine and Skype.
But I am not 100% sure what is left in deep of the config.  

Once again 
Thank you.
michael

---

