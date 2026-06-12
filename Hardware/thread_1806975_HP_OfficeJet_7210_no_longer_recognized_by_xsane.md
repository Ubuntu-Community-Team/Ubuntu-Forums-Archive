---
title: "HP OfficeJet 7210 no longer recognized by xsane"
date: 2011-07-18
forum: Hardware
---

### Post by rebeltaz on 2011-07-18
I have an HP OfficeJet 7210 scanner/printer that I have been using for a couple of years with no problems. The other day, I tried to install a couple of programs. I forget which now, but neither one did what I needed so I removed them with apt-get. As soon as I did that, my printer was no longer recognized.

I was able to get the printer working again by reinstalling the cups print-server package and recreating the link to the printer. 

xsane is still telling me that "no devices [are] available." I have removed xsane, libsane and libsane-extras and reinstalled then with no effect. I also noticed that, while dpkg reported that hplip was installed, aptitude could not reinstall it saying that it was not installed. So I installed hplip and hplip-gui using apt-get. 

I then created a new printer link using System-Administration-Printing with a different name. I did notice that the first printer I created, before I installed hplip, is showing up as a 'network printer' whereas the new printer I created, after hplip, is showing up as simply 'printer'. Both times I add the printer from the Network Printer dropdown menu so...

I cannot think of anything else to try, so any help or advice would be great. Thanks....

** EDIT **
OK, I ran HPLIP Toolkit and ran the the Setup from within that to install yet another printer. That did the trick - now xsane is seeing the scanner.

I never had to to that when I first installed this printer. And now I have an HP icon up in the system tray that I never had there before. I would really like to know what happened originally....

Thanks.

---

