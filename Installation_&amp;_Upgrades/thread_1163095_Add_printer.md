---
title: "Add printer"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by kisumisu on 2009-05-18
Im running ubuntu 9.04.
My problem is that I can not add any printer...when I go to "system -> administration -> printing.
I try to go new printer, but the printer menu is grey and nothing to do :-(
When I try connect it only fails....
when I go with browser to [http://localhost:631](http://localhost:631)
It only says Failed to Connect......
What can possibly be wrong?

Because it is a hp printer I tried install hp software, it says find ppd file...I found file and added "add printer" but it says "wrong password" Can not start Cups....

I have another computer where there is no problem to connect this printer with ubuntu 9.04. So I have messed up with something, but what? :-(

Sorry for my bad english and hope someone understand and can help me out....

---

### Post by coffeecat on 2009-05-18
> **kisumisu said:**
> I try to go new printer, but the printer menu is grey and nothing to do :-(
When I try connect it only fails....
when I go with browser to [http://localhost:631](http://localhost:631)
It only says Failed to Connect......
What can possibly be wrong?

That sounds as though cups (Common Unix Printing System) is not installed, or broken. Have a look in Synaptic and see if cups is installed. If it is, try reinstalling. In my system there are 7 cups-related packages installed and printing is working fine. If just reinstalling cups by itself doesn't help, have a look in Synaptic in the other machine to get the list of the seven packages and reinstall them all.

---

### Post by kisumisu on 2009-05-19
Yes I compared these computers with Synaptic pagage manager and everything was same, I re install cups. Nothing happened, even restarted computer...nothing!
But thank you anyway for your help, because what I did was compared files in cups folder and the non working computer did not have all files. Cups was broken as you say!
What I did was sudo nautilus
then I copy all files in Cups folder! And the missing /etc/ssl/certs/ssl-cert-snakeoil.pem and /etc/ssl/private/ssl-cert-snakeoil.key 
Now everything works really fine! ):P
Don't understand why not all files where there even when i reinstall...but anyway now it works and I'm happy! :D

---

### Post by nialui on 2009-05-21
@kisumisu:

i have the same problem as yours, but i don't have other computer for me to copy those file...

could you at least upload those file in some server for me? please... :D:D

oh, and what is the permission to these file?

thank you...

---

### Post by kisumisu on 2009-05-24
nialui

Hello!
Yes I could copy, but you will find same files if you run the "live disc" then you can copy from there.
Run Live disc....then you can copy files from there.
I hope I can help...It seems that even other ppl then have this problem :-)

---

### Post by nialui on 2009-05-24
it works like a charm!!

Finally I can get over this after 2 weeks searching for the solution, thanks kisumisu... :D:D:D

---

### Post by kisumisu on 2009-05-25
start live cd
configure printer in there system admin printer
Add your printer
then save and exit
Go to accesories Terminal
write sudo nautilus
Navigate to ETC/CUPS
Mark cups folder right click choose permissions
file access read and write
folder access create and delete
file access read and write
folder access create and delete
file access read and write
apply permission to enclosed files

and then you copy the folder "CUPS"
paste it for example on USB memory or something other like external hardrive

Go to /etc/ssl/certs/
and copy ssl-cert-snakeoil.pem
paste it for example on USB memory or something other like external hardrive

Go to 
/etc/ssl/private/
Mark private folder right click choose permissions
file access read and write
folder access create and delete
file access read and write
folder access create and delete
file access read and write
apply permission to enclosed files

and then you copy the folder "PRIVATE"
paste it for example on USB memory or something other like external hardrive

And now you shut down Live Ubuntu and start your computer with your real Ubuntu and do all these things reverse...
Go to Terminal sudo nautilus
copy and paste files from USB or external harddrive to your system...Cups
to /ETC/
and so on.......

If someone have easier way you can explain here too :-)
I Hope this will work for you...

---

### Post by kisumisu on 2009-05-25
[nialui]("http://ubuntuforums.org/member.php?u=839741")
oh now I see it already worked for you...Nice :popcorn:
I did not read it until now :P But maybe will this tutorial help someone else!

---

