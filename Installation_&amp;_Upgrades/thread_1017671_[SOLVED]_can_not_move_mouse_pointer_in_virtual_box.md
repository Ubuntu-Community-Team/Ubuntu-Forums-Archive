---
title: "[SOLVED] can not move mouse pointer in virtual box.........!!!!"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by chinmaya_n on 2008-12-21
I have recently installed " virtual box ".... and i installed Windows 2000 server edition on it.

It all went cool............. The installation was successful.
The problem is



1.when Every time i  press any click on the VB screen it is showing to capture the image and i can not move the mouse pointer which is inside the windows

2. i cannot move the mouse pointer inside it.... i'm just abled to access throug keyboard only. How can i move the mouse pointer in virtual box?

3.Even when i attemted to have it full screen it is just showing on a small rectangular box. How can i get it in to full screen?

Plz any one help me..........This is the first time i am using VB..... Plz be in a quite explanatory way....... !!!

---

### Post by trendyabinash on 2008-12-21
Sir you don't have to post the same topic twice, ubuntu staff will help you please be patient.

---

### Post by albinootje on 2008-12-21
> **chinmaya_n said:**
> I have recently installed " virtual box ".... and i installed Windows 2000 server edition on it.

It all went cool............. The installation was successful.
The problem is



1.when Every time i  press any click on the VB screen it is showing to capture the image and i can not move the mouse pointer which is inside the windows

2. i cannot move the mouse pointer inside it.... i'm just abled to access throug keyboard only. How can i move the mouse pointer in virtual box?

3.Even when i attemted to have it full screen it is just showing on a small rectangular box. How can i get it in to full screen?


You should install the VirtualBox Guest Additions. 
That will remove the mouse-capture, and let you have full screen.

Here's a howto for XP guest :
[http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/)

---

### Post by chinmaya_n on 2008-12-21
> **trendyabinash said:**
> Sir you don't have to post the same topic twice, ubuntu staff will help you please be patient.

Actually i didnt posted this twice........... it first showed server was down........ So tried twice it might have posted at that time ..........!!!!!!!!!

---

### Post by chinmaya_n on 2008-12-21
I just tried as u gave in the link , Albinootje...

it is showing an error msg in a small window as :

" An error occured while installing!
 please refer to the file log file under 'c:\program files\sun\xVM Virtual Box Guest Auditions\install_ui.log' for more information. "

When i checked the location there is no file with the name install_ui.log....

---

### Post by albinootje on 2008-12-21
> **chinmaya_n said:**
> I just tried as u gave in the link , Albinootje...

it is showing an error msg in a small window as :

" An error occured while installing!
 please refer to the file log file under 'c:\program files\sun\xVM Virtual Box Guest Auditions\install_ui.log' for more information. "

When i checked the location there is no file with the name install_ui.log....

Do you have a dual-boot machine ?
That would be c:\program files\sun\xVM Virtual Box Guest Auditions\install_ui.log inside the Windows guest in VirtualBox.
Did you check there ?

---

### Post by chinmaya_n on 2008-12-21
I'm having dual boot in the hard disk. But not in the Virtual Machine. I checked in it thrice ..... but i could not found that file inside the windows guest either.

It gave an option that to ignore it ........ Then i marked the ignore option ....... then the installtion went for some time and it showed a "File Progress" Window, with a progress bar and 'cancel button'. But the progress is not taking place.... Hours together it is showing same window with out any progress..!!!!!

Plz any one help me ......!!!!!!

---

### Post by albinootje on 2008-12-21
> **chinmaya_n said:**
> I'm having dual boot in the hard disk. But not in the Virtual Machine. I checked in it thrice ..... but i could not found that file inside the windows guest either.

Hmm, weird :(
Can you try installing the Guest Additions again ?
You need to be running your Windows2000 guest, and then start the Guest Additions installation.
Do you have enough disk space left in the Windows2000 guest ?

---

### Post by chinmaya_n on 2008-12-21
I have enough space on my Windows 2000 guist. 

I tried reinstalling guest auditions twice . It gave the same result, no change..!!

When the first time i tried it didnt asked me as u gave in the link that whether to download cd image. It directly showed the set up window..!! 

But this time i observed something new it showed "The signature on the software package you want to install is invalid. The software is  not signed properly."

---

### Post by albinootje on 2008-12-21
> **chinmaya_n said:**
> 
But this time i observed something new it showed "The signature on the software package you want to install is invalid. The software is  not signed properly."

Do you get that during the Guest Additions installation ?
If so, you need to accept that, and continue.

---

### Post by chinmaya_n on 2008-12-22
When i contined, it gave a blank small window as mentiond in previous  posts that a status bar and a cancel button .......

It has no progress  in the status bar...

---

### Post by chinmaya_n on 2008-12-22
I dont know how but ........ this time i got it . It didn't gave me any error message........ the process went cool.....

Thanx 4 ur help.

---

