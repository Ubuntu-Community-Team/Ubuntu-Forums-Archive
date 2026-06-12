---
title: "cups-pdf postprocessing troubleshooting"
date: 2008-08-13
forum: General Help
---

### Post by xaviel on 2008-08-13
I ran into some trouble using the postprocessing feature of cups-pdf on Ubuntu 8.04. My postprocessing scripts would not execute. It turns out cups-pdf doesn't like AppArmor. And AppArmor is up and running by default on Ubuntu 8.04. Heres my solution: 

A simple "sudo aa-complain /etc/apparmor.d/*" fixes the problem and your postprocessing scripts can execute properly.  

Cheers!

---

### Post by kaibob on 2008-08-13
> **xaviel said:**
> I ran into some trouble using the postprocessing feature of cups-pdf on Ubuntu 8.04. My postprocessing scripts would not execute. It turns out cups-pdf doesn't like AppArmor. And AppArmor is up and running by default on Ubuntu 8.04. Heres my solution: 

A simple "sudo aa-complain /etc/apparmor.d/*" fixes the problem and your postprocessing scripts can execute properly.  

Cheers!

I've been playing around with the postprocessing function of cups-pdf and thus far I've had success with scripts that prompt for the PDF file name and that open the created PDF file in evince. I followed the general procedure outlined in post 2 of the following thread, although I only used a single script without the PY and XML files:

[http://ubuntuforums.org/showthread.php?t=837257](http://ubuntuforums.org/showthread.php?t=837257)

I did a bit of research on the solution suggested by xaviel and found the following on the aa-complain toggle: 

*aa-complain toggles the mode of an AppArmor profile from enforce to complain. Exceptions to rules set in a profile are logged, but the profile is not enforced.*

[http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/apparmor_sec_aa_whatimm_tools.html](http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/apparmor_sec_aa_whatimm_tools.html)

I don't have the knowledge to determine if changing the AppArmor profile from enforce to complain mode is a security issue, but it does seem a concern. I added my postprocessing script to usr.sbin.cupsd to allow it to successfully execute, but AppArmor issued a warning when first restarted about passing an argument from cups-pdf to the script. This would seem a smaller security concern but, once again, I lack the knowledge to know if this is the case. Hopefully, those with more experience in this area will suggest the best way to implement postprocessing with cups-pdf. It is good to know that it does work, though.

---

### Post by DjC1982 on 2010-04-12
Thanks xaviel 

This became an issue for me after some one installed some updates on my old printer server. Spent ages trying to fix it and this was the issue.  

 What really annoys me is the fact something was been blocked wasn't logged anywhere. The cups-pdf log showed it executed the script and finished with out an error. 

I didnt think it was an error in my PostProcessing scripts.

Thanks again,

David

---

### Post by dwitkin on 2011-03-22
Kaibob,

You mention you were able to create a post-processing script to open evince after creating a PDF using cups. Would you mind sharing your script? I am trying to do the same thing but have been unsuccessful in getting CUPS to process the script.

Thanks. 


> **kaibob said:**
> I've been playing around with the postprocessing function of cups-pdf and thus far I've had success with scripts that prompt for the PDF file name and that open the created PDF file in evince. I followed the general procedure outlined in post 2 of the following thread, although I only used a single script without the PY and XML files:

[http://ubuntuforums.org/showthread.php?t=837257](http://ubuntuforums.org/showthread.php?t=837257)

I did a bit of research on the solution suggested by xaviel and found the following on the aa-complain toggle: 

*aa-complain toggles the mode of an AppArmor profile from enforce to complain. Exceptions to rules set in a profile are logged, but the profile is not enforced.*

[http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/apparmor_sec_aa_whatimm_tools.html](http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/apparmor_sec_aa_whatimm_tools.html)

I don't have the knowledge to determine if changing the AppArmor profile from enforce to complain mode is a security issue, but it does seem a concern. I added my postprocessing script to usr.sbin.cupsd to allow it to successfully execute, but AppArmor issued a warning when first restarted about passing an argument from cups-pdf to the script. This would seem a smaller security concern but, once again, I lack the knowledge to know if this is the case. Hopefully, those with more experience in this area will suggest the best way to implement postprocessing with cups-pdf. It is good to know that it does work, though.

---

### Post by kaibob on 2011-03-23
dwitkin

The general procedure I followed is outlined in the following post:

[http://ubuntuforums.org/showthread.php?t=893968](http://ubuntuforums.org/showthread.php?t=893968)

To open the PDF file in evince, you would delete the two lines of the sample script (they begin with "PDFNAME" and "mv") and insert:

```
evince "$CURRENT_PDF"
```

I did this over 2 years ago, and it may not work with a current version of Ubuntu. But it doesn't take much time to give it a try.

---

### Post by cprevoe on 2012-07-05
Using aa-complain apparmor.d/* might be  overkill as you're basically telling apparmor not to enforce anything  else configured there as well.

Instead the following will allow your postprocessing script to run without disabling  anything extra (though also without protecting cups properly).
```
aa-complain /etc/apparmor.d/usr.sbin.cupsd
```An even better solution is to add your script to the apparmor config for cups-pdf. In my case, created my script /usr/bin/cups_post.sh and added the following to the /usr/lib/cups/backend/cups-pdf block near the end of /etc/apparmor.d/usr.sbin.cupsd.
```
/usr/bin/cups_post.sh rPx, 
```

The rPx grants read and execute which allows the script to run unconstrained in a scrubbed environment. 

More info on the format of the apparmor config is available in 'man apparmor.d'

Hope this helps someone.

---

