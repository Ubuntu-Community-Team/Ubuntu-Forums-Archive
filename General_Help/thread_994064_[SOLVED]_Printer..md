---
title: "[SOLVED] Printer."
date: 2008-11-26
forum: General Help
---

### Post by Dyffo on 2008-11-26
I am trying to install a Brother MFC 3240 C printer directly on to my computer which is running Intrepid 8.10.The computer recognises the printer but shows no direct drivers to support it. I have been to the Brother Web site - this shows Linux / Ubuntu 8.10 drivers for this printer which I have downloaded but I just cannot get the thing  to recognise these drivers or to work !!!!!!!!!!!!! any ideas.

---

### Post by roger_1960 on 2008-11-26
Hi

Search synaptic for 'brother' and install the package(s) (brother-cups-wrapper-extra etc) which lists your printer in the description.  Then paste

 [http://localhost:631/admin](http://localhost:631/admin) 

into firefox browser and use the add printer option.  Worked really well for me with a brother printer and 64bit ubuntu.

---

### Post by nikgare on 2008-11-26
Try this link, adn also the page that links from it.

[http://ubuntuforums.org/showthread.php?t=845609](http://ubuntuforums.org/showthread.php?t=845609)

---

### Post by Dyffo on 2008-11-27
Hi Guys - thanks all done and works fine - never realised that you could get drivers from Synaptic !!!!

---

