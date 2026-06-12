---
title: "No DVD Drive detected in nautilus"
date: 2010-03-06
forum: Hardware
---

### Post by benrufus on 2010-03-06
Hi

I have a DVD drive on my laptop but Ubuntu doesn't show it in Nautilus and i cant play CDs or DVDs. Any ideas would be greatly appreciated! It may be that the drive doesn't work but I don't know how to find out..... My mum also has the same problem on her system but her DVD drive definitely did work before installing Ubuntu so it would be great to get hers working at least. Thanks a lot.......

---

### Post by byStanderone on 2010-03-06
give this a try: sudo eject /dev/scd0 (an old trick from the forums, hope it works for you)

---

### Post by benrufus on 2010-03-06
> **byStanderone said:**
> give this a try: sudo eject /dev/scd0 (an old trick from the forums, hope it works for you)

Hi

this is the output i got

ubuntu@ubuntu:~$ sudo eject /dev/scd0
[sudo] password for ubuntu: 
eject: unable to find or open device for: `/dev/scd0'
ubuntu@ubuntu:~$

---

### Post by byStanderone on 2010-03-06
...i see, you will have to do it the medibuntu way:

   1.  Load in your browser this url: [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg). This is the repository key file.
   2. From your browser menu select “File -> Save page as..” and save it somewhere temporarily, for example on your desktop.
   3. Now from the Ubuntu main menu, select “System -> System administration -> Software sources”. It will ask for your user password.
   4. In the “Other software” tab, press the add button, paste the following line and click “Add source”:

      deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
   5. Change to the “Certificates” tab, press “Add key from file” and select the key file you have saved previously in your system.
   6. Click close and you are done. It will ask you to refresh the software sources catalog, so select to refresh it.


-courtesy of eval(life) doing it the gui way

---

### Post by benrufus on 2010-03-08
> **byStanderone said:**
> ...i see, you will have to do it the medibuntu way:

   1.  Load in your browser this url: [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg). This is the repository key file.
   2. From your browser menu select “File -> Save page as..” and save it somewhere temporarily, for example on your desktop.
   3. Now from the Ubuntu main menu, select “System -> System administration -> Software sources”. It will ask for your user password.
   4. In the “Other software” tab, press the add button, paste the following line and click “Add source”:

      deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
   5. Change to the “Certificates” tab, press “Add key from file” and select the key file you have saved previously in your system.
   6. Click close and you are done. It will ask you to refresh the software sources catalog, so select to refresh it.


-courtesy of eval(life) doing it the gui way


Hi 

I have installed Medibuntu but i still have no DVD Drive!! Seems like a hardware problem maybe?? How would i tell?

thanks

---

### Post by byStanderone on 2010-03-13
hi,

sorry...was out of town the last few days. sin you're on a laptop, a bit hard to swap drives to eliminate the problem, but have your tried installing the ubuntu-restricted-extras ? your needed codec might just be there...easier than changing drives, tho i hope you've came to a solution by this time.

---

### Post by benrufus on 2010-03-14
hi Standerone, yeah ive got the restricted extras installed already and still it dosent work, but i think its the drive that is knackered on my machine! Thats a great idea though for my mums machine, she has 9.04 installed but she can only play CDs even though she has a DVD drive, do you think the restricted extras will help her get DVDs to work?

thanks

---

### Post by byStanderone on 2010-03-14
...yup, no harm in trying the restricted extras plus the medibuntu package.

---

