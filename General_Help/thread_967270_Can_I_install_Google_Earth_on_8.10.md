---
title: "Can I install Google Earth on 8.10"
date: 2008-11-01
forum: General Help
---

### Post by Buschbarber on 2008-11-01
Google Earth does not appear in Synaptic, on Ubuntu 8.1. Can it be installed?

---

### Post by dcstar on 2008-11-01
> **Buschbarber said:**
> Google Earth does not appear in Synaptic, on Ubuntu 8.1. Can it be installed?

There should be a package that fetches and compiles the latest binary into a deb for you via terminal commands:

googleearth-package

---

### Post by soro2005 on 2008-11-01
It's on Medibuntu. go to [www.medibuntu.org](www.medibuntu.org) and follow the instructions there.

---

### Post by Buschbarber on 2008-11-01
I am not up to speed on Command Line stuff, yet, Can you be more specific as to the commands I need to type in to download and install Googleearth?

P.S. I have marked some threads as Solved and others left Open, but I will try to be diligent about that!!

---

### Post by dcstar on 2008-11-01
> **Buschbarber said:**
> I am not up to speed on Command Line stuff, yet, Can you be more specific as to the commands I need to type in to download and install Googleearth?

P.S. I have marked some threads as Solved and others left Open, but I will try to be diligent about that!!

[http://ubuntuforums.org/showthread.php?t=601272](http://ubuntuforums.org/showthread.php?t=601272)

---

### Post by soro2005 on 2008-11-01
> **Buschbarber said:**
> I am not up to speed on Command Line stuff, yet, Can you be more specific as to the commands I need to type in to download and install Googleearth?

P.S. I have marked some threads as Solved and others left Open, but I will try to be diligent about that!!

Do yourself a favor and get it from Medibuntu. There is no point in compiling it, you're going to get an updated version every time there is one. You might want to enable the Medibuntu repositories, anyway, for media codecs, DVD viewing, fonts, etc. Once you have the repository in your list, Google Earth will be in your Synaptic. Instructions at [www.medibuntu.org](www.medibuntu.org).

---

### Post by Glugglug on 2008-11-01
You can download it from the Google earth site   if you have the Google search page up  along the top of the page click on the more drop down list and at the bottom   even more     Google earth comes up on that page.

It downloads as a bin file  extract it   then create archive it should appear on desktop as tar gz .

---

### Post by Buschbarber on 2008-11-01
Thanks to all!! I installed the Repository and Installed Google Earth 4.3. The only problem is that when the Earth displays in the window, it displays slowly and very low res. In 30 sec it still had not enlarged to full size and only bits and pieces of the image were normal. The rest of the application looked normal.

I also installed the libdvdcss2 and the w32codecs. I receive a number of .wmv files in emails and Totem, the default player, could not play them,

---

### Post by soro2005 on 2008-11-01
> **Buschbarber said:**
> Thanks to all!! I installed the Repository and Installed Google Earth 4.3. The only problem is that when the Earth displays in the window, it displays slowly and very low res. In 30 sec it still had not enlarged to full size and only bits and pieces of the image were normal. The rest of the application looked normal.

I also installed the libdvdcss2 and the w32codecs. I receive a number of .wmv files in emails and Totem, the default player, could not play them,

It'll start quicker once it has loaded the first frames into cache, and some of the places you normally go to. It's a huge amount of data, particularly for slower connections. :-)

---

### Post by Buschbarber on 2008-11-18
It never loaded properly. It does not run properly with the Onboard Intel video adapter that I have to use. It just slowly tries to load the graphic of the Earth, but only displays a hollow globe with lines for a shell and only bits and pieces of the image. 8.10 will not allow me to use my Nvidia 6200 OC card drivers.

When I install the Google Earth, on the same PC, under Ultimate 1.9, it won't load at all and gives me an error that the Graphics card cannot be detected, even though I am using the Restricted Nvidia drivers.

---

