---
title: "Deskjet D1600 problems?"
date: 2010-04-30
forum: Hardware
---

### Post by jmate24 on 2010-04-30
I just bought a new printer this month and so far it will not print under lucid but it was printing before in karmic...

does anyone have any suggestions as to how I can fix this problem?

it is a HP deskjet d1660 and the driver is... HP Deskjet d1600 Series hpijs, 3.10.2 [en] (current)

---

### Post by jmate24 on 2010-05-02
i know that it is the driver... but there is no other driver besides the one that is listed. it works in windows but not in (x)ubuntu. where can i go to file a bug report on the driver of the printer that is provided by (x)ubuntu? i am using (x)ubuntu 10.04 lucid

---

### Post by mr_niceguy on 2010-05-03
> **jmate24 said:**
> I just bought a new printer this month and so far it will not print under lucid but it was printing before in karmic...

does anyone have any suggestions as to how I can fix this problem?

it is a HP deskjet d1660 and the driver is... HP Deskjet d1600 Series hpijs, 3.10.2 [en] (current)

I had to use the automatic installer from HP.

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Removed the printer first.

Had a little weirdness at the end of the process. Basically the drivers were successfully replaced but the install gui did not allow me to "Add Printer" and I had to quit at that point.

Running "sudo hp-setup" allowed the process to complete.

---

### Post by jmate24 on 2010-05-06
Thanx.

---

### Post by Icarus315 on 2010-05-06
Thank you mr_niceguy, that got me up and running although I didn't have to sudo hp-setup at the end, that just worked! :D

---

### Post by stan kingston on 2010-05-11
I  also had the same problem with my HP D1660 printer using Ubuntu 10.04. Then I was directed to your post. I used the HP Automatic installer and my printer now works OK.
This procedure also got my HP Scanjet 3970 working, so I am very pleased.
I thank you Mr. Niceguy, very good of you to take the trouble to post.
Kind regards Stan

---

### Post by flyfishingphil on 2010-05-12
> **mr_niceguy said:**
> I had to use the automatic installer from HP.

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Removed the printer first.

Had a little weirdness at the end of the process. Basically the drivers were successfully replaced but the install gui did not allow me to "Add Printer" and I had to quit at that point.

Running "sudo hp-setup" allowed the process to complete.
Thank you so much mr_niceguy for your info. Just purchased a D1660, to replace a Lexmark that was unusable, and was about to give up on getting the HP to work until I stumbled across this page. Glad I did. It's up and working fine.

I had been there before but kept getting the "not compatible with Ubuntu 10.04" notice. Uninstalling and unplugging seemd to overcome that.

Thanks again for making it easy to follow/do.

Maybe this should be done as a sticky!

---

### Post by rp3 on 2010-05-22
> **flyfishingphil said:**
> Thank you so much mr_niceguy for your info. Just purchased a D1660, to replace a Lexmark that was unusable, and was about to give up on getting the HP to work until I stumbled across this page. Glad I did. It's up and working fine.

I had been there before but kept getting the "not compatible with Ubuntu 10.04" notice. Uninstalling and unplugging seemd to overcome that.

Thanks again for making it easy to follow/do.

Maybe this should be done as a sticky!

Solved the issue with a new install at my sisters who is a short flight away, glad I got this working whilst I was there... :)

:)

---

### Post by squidpotion on 2010-06-26
Edit: Nevermind, I got it running. Idiot me failed to note that the terminal was case-sensitive.

---

### Post by warpasylum on 2010-08-01
Hey, thanks alot man.  My printer's working perfectly now.

---

### Post by volaer on 2010-08-09
Or, you can try this. I used this to solve mine:

[http://bloggervince.blogspot.com/2010/08/how-to-install-hp-d1660-in-ubuntu.html]("http://bloggervince.blogspot.com/2010/08/how-to-install-hp-d1660-in-ubuntu.html")

---

### Post by triscones on 2010-10-19
Hi,

when trying to install the newer HP driver for my d1660 deskjet I am getting the messege: 

Could not open the file /home/neptune/Downloads/hplip-3.10.9.run.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

Does anyone know what to do here?? 

Cheers, Tristan

---

### Post by triscones on 2010-10-19
Hey:

After downloading the newer driver from HP Could not open the file /home/neptune/Desktop/hplip-3.10.9 (1).run.

followed by: 
gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

and an option to select the encoding.

Any suggestions?  

Thanks

---

### Post by rccurtright on 2010-10-23
> Or, you can try this. I used this to solve mine:

[http://bloggervince.blogspot.com/201...in-ubuntu.html](http://bloggervince.blogspot.com/201...in-ubuntu.html)

Thanks volaer.

Worked for me too. I tried a bunch of other stuff but that finally did the trick. Already had hplip and CUPS, ran hp-install nothing worked.

Irritating thing was my XP install on virtualbox could use the printer and Ubuntu couldn't.

All good now. Thanks again!

---

### Post by boddhisatva on 2011-01-03
I've just bought the printer, believing it would run on Ubuntu after reading a few posts. I've tried all the suggestions, but it won't budge on Maverick. The only thing it does from hplip-gui is calibrate the cartridges, and that's the only time I actually see the printer printing something. It also seems to do the the cartridge cleaning, but it doesn't print out any output. The boggervince solution above doesn't work either - the older driver is not on the list.
I'm on Maverick 64bit.

---

### Post by Yellow Pasque on 2011-01-03
> **triscones said:**
> Could not open the file /home/neptune/Downloads/hplip-3.10.9.run.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

Does anyone know what to do here?? 

Make the file executable and execute it (this will probably get you a lot farther than trying to open it in a text editor).
```
cd ~/Downloads
chmod +x hplip-3.10.9.run
./hplip-3.10.9.run
```

---

### Post by egorchik007 on 2011-03-15
> **mr_niceguy said:**
> I had to use the automatic installer from HP.

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Removed the printer first.

Had a little weirdness at the end of the process. Basically the drivers were successfully replaced but the install gui did not allow me to "Add Printer" and I had to quit at that point.

Running "sudo hp-setup" allowed the process to complete.
the problem is, that in hp-setup is no ppd file for my model (deskjet 3420). if i select the another ppd, the story in the 1st post begins again!some noise, moving - but no ink. I think i just need the correct .ppd file. Please, help me - can you upload this file for me?

---

### Post by egorchik007 on 2011-03-15
oh, sorry. i have found the correct ppd, but there is no ink anyway.
i have done all by the instructions - what is the problem?
Everything is OK on Windows.
help me please. (i can ever use TeamViewer, if you will have time to help me).
Thank you very much!

---

### Post by nixor01 on 2011-05-01
Works great, Thanks mr_niceguy

---

### Post by mikeyc45 on 2011-06-09
Thanks Volaer, that worked for me too.  I tried all the previous advice and none of it worked.  I'm on 9.10 with an HP D1660.  Mine was working, but after an update to the latest HPLIP 3.11.5 everything came to a grinding halt.

I hope Vince doesn't mind, but I though I'd post his solution:

   1. Go System> Administration> Printing
   2. Right Click Deskjet d1600 series
   3. Click properties
   4. Click Settings
   5. "Change" in Make and Model bar  ....it will search for driver
   6. Click HP, click deskjet 1600 series
   7. Choose the driver HP Deskjet D1600 Series, hpcups 3.10.2 (or whatever hpcups driver is installed)

---

### Post by welshmike on 2011-08-31
Thanks mr_niceguy

I somehow lost use of my printer on Lucid. Not sure when it last worked maybe on Karmic.
Using the info in your message it is now working again.

Mike

---

