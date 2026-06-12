---
title: "[SOLVED] Installing the latest version of OpenOffice"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by crimlaw on 2009-01-11
After installing 8.10 and opening OpenOffice, I realised that it is not the latest version.  I tried to follow the "Help" menu in OpenOffice to get an automatic upgrade, but I did not have that option.  

I tried to download it from the website.  I extracted the files, but now I can't figure out how to install it over my older version.  

Can anyone help?  Does anyone know code I can copy into a terminal and update automatically?  I am still new to terminal language.  

Thanks!!!

---

### Post by kranny on 2009-01-11
Go to System > Administration > Software Sources
Go to Third-Party software  press the Add Button and paste the text below:

    ```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main 
```

Press Add souce to confirm then Close and after this press Reload for changes to take place.You will now see the update icon in the upper panel. Double click to open the update manager.Run the updates and everything should now be done.

---

### Post by crimlaw on 2009-01-11
worked out like a charm.  Thanks

---

