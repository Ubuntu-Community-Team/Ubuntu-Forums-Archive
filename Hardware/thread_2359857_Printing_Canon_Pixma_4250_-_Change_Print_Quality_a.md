---
title: "Printing Canon Pixma 4250 - Change Print Quality and Grayscale Option"
date: 2017-04-28
forum: Hardware
---

### Post by woody22075 on 2017-04-28
Dear All,

On my previous install of Ubuntu I had configured my Canon Pixma printer to give me an option of 1-4 print quality and a checkbox for grayscale. Having done a fresh install, I don't recall how to achieve this. Any thoughts? (Running 16.04).

Thank you!

M.

---

### Post by pdc on 2017-04-28
I rather think that some used to advise going to Job Options; when one right-clicks on the icon for your 4250; and one could add ```
CNGrayscale
```

here are a few links that offer that solution; and others; that involve editing the ppd file 

[https://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/](https://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/)

[https://askubuntu.com/questions/81500/how-to-print-in-black-and-white-for-canon-printers](https://askubuntu.com/questions/81500/how-to-print-in-black-and-white-for-canon-printers)

[https://gist.github.com/tomsquest/1263877](https://gist.github.com/tomsquest/1263877)

_________
recently this thread ran in this forum [https://ubuntuforums.org/showthread.php?t=2354789&highlight=grayscale](https://ubuntuforums.org/showthread.php?t=2354789&highlight=grayscale) and for an HP one had to edit the ppd file: details in the thread

________
for print quality, I rather think one also had to edit the ppd file: if you google on that; one could then add a series of options that suited what one wanted; I am afraid I have just left the printer as is: ca marche assez

Turboprint offer very good drivers and for your device, you can see they quote a range of values [http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MG4250](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MG4250)

---

### Post by woody22075 on 2017-04-29
Thank you for the reply but I am interested in being able to change print quality with respect to colour and grayscale. I wish I could remember how I did it before but perhaps someone does?

Thanks again!

m.


> **pdc said:**
> I rather think that some used to advise going to Job Options; when one right-clicks on the icon for your 4250; and one could add ```
CNGrayscale
```

here are a few links that offer that solution; and others; that involve editing the ppd file 

[https://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/](https://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/)

[https://askubuntu.com/questions/81500/how-to-print-in-black-and-white-for-canon-printers](https://askubuntu.com/questions/81500/how-to-print-in-black-and-white-for-canon-printers)

[https://gist.github.com/tomsquest/1263877](https://gist.github.com/tomsquest/1263877)

_________
recently this thread ran in this forum [https://ubuntuforums.org/showthread.php?t=2354789&highlight=grayscale](https://ubuntuforums.org/showthread.php?t=2354789&highlight=grayscale) and for an HP one had to edit the ppd file: details in the thread

________
for print quality, I rather think one also had to edit the ppd file: if you google on that; one could then add a series of options that suited what one wanted; I am afraid I have just left the printer as is: ca marche assez

Turboprint offer very good drivers and for your device, you can see they quote a range of values [http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MG4250](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MG4250)

---

### Post by gsahli on 2017-04-29
Use the cups internal admin web page:
[https://askubuntu.com/questions/296594/change-default-printing-settings](https://askubuntu.com/questions/296594/change-default-printing-settings)
(on 16.04 and newer, you may need to restart cups after making sure you are in group lpadmin)

---

### Post by woody22075 on 2017-04-29
still not doing it--i would like to have the old 1-4 quality and grayscale options. any more thoughts?

thanks again for all the posters!

m.

---

### Post by pdc on 2017-04-29
go on; get Turboprint for yourself: you deserve it; it gives wonderful control of a variety of parameters; treat yourself

---

