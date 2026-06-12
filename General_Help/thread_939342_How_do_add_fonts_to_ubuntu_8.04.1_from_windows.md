---
title: "How do add fonts to ubuntu 8.04.1 from windows"
date: 2008-10-05
forum: General Help
---

### Post by bluebirday on 2008-10-05
Please note that I tried to use program fontforg to import some fonts
from windows font folder to Ubuntu font folder but the said program
does not work properly although I used it with Ubuntu 8.04 and was
doing well.
could you help me to advise another program do the same function
or to tell me how to be able to get a permission to add the required
fonts manually to _**consolefonts**_ folder 

Best Regards

---

### Post by Blackwolf_Oz on 2008-10-06
You can install the MS core fonts by installing the msttcorefonts package. To do this, enable the &#8220;Universe&#8221; component of the repositories. This is done by default in Feisty. After you do that, use the following command from the command line:

$sudo apt-get install msttcorefonts

This will give you the core fonts, but if there are other TrueType fonts that you want installed, it is as easy as copying the font files to the ~/.fonts/ directory.

After installing new fonts, you will have to log out and log in again to be able to see and use the new fonts. If you want to avoid this, you can regenerate the fonts cache by issuing the following command:
$sudo fc-cache -fv

---

