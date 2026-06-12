---
title: "epson stylus nx415 wont install"
date: 2009-08-29
forum: Hardware
---

### Post by countryjake on 2009-08-29
i have been attempting to install this printer in jaunty and i have all the necessary files to install it, however, when i try to install pips lite, it says it doesnt have the necessary dependencies, which is libltdl3, but i have libltdl7 installed!

here is where the files are found:
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

please help! i hate using windows and really want to get this printer to work on linux!

---

### Post by countryjake on 2009-09-01
bump

---

### Post by countryjake on 2009-09-01
please!! i really need help with this!!

---

### Post by countryjake on 2009-09-01
i tried to reinstall the printer again, and i feel like im getting so close but i end up with the same damn error! it says the the pipslite-wrapper failed and i dont know what to do! CUPS recognizes the printer and its correct driver and everything! could it be that pipslite is the problem and i should downgrade it? please help!

---

### Post by radioraheem on 2009-09-13
I'm also having this problem, and am also considering switching over to windows again just because I'm tired of this B.S.

If anyone finds a solution I'd appreciate a heads up.

Thanks

---

### Post by countryjake on 2009-09-13
i actually figured out how to perfectly install this!
the main problem is with the PIPS-Lite! it doesnt install correctly and then the printer doesnt work! I will send you a PM on how to get this printer working correctly!

---

### Post by ftecapo on 2009-09-14
would you please also tell me how to install it correctly? i´ve had the same problem for ages.
thanks a lot

---

### Post by countryjake on 2009-09-15
[FONT=monospace]go to my new thread on how to get this printer (and pipslite) working:
[http://ubuntuforums.org/showthread.php?p=7947793](http://ubuntuforums.org/showthread.php?p=7947793)
[/FONT]

---

### Post by imretokyo on 2009-10-20
> **countryjake said:**
> when i try to install pips lite, it says it doesnt have the necessary dependencies, which is libltdl3, but i have libltdl7 installed!

I found an another solution for this problem. 

Following the [_FAQ_]("http://avasys.jp/eng/linux_driver/faq/id000613.php") of the avasys website.

First I tried to follow Countryjake`s thread. I have a different printer pm-t990, which doesn`t make a big difference i guess. 

But avasys doesn`t provide ppd file for my printer. While I was looking for the ppd file on their website, I found the FAQ.

I followed the FAQ description about installing libltdl3. When I was done, I checkd synaptic if there is any change, but there was none. Still the libltdl7. Anyway I went back to the avasys readme file for my printer`s deb. And tried to install my deb file again, and everything was ok that time. 

I can print documents, but I didn`t try to print photos nor the scanning yet.

---

