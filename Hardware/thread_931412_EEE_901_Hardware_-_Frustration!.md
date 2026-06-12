---
title: "EEE 901 Hardware - Frustration!"
date: 2008-09-27
forum: Hardware
---

### Post by DrSasaroli68 on 2008-09-27
I really cannot judge whether this is the best suited place for this subject but I have been greatly helped by this forums so H hope that ideas will once more surface and maybe other people will also be helped!


Situation goes like this: Mother owned a EEE 900 and beeing quite amazed with it and it's out of the box compatibility with BackTrack 3 and i ordered an EEE 901 myself. Unfortunately it was a hasty and in retrospect bad  decision. 
Situation: The bloody thing is incompatible and buggy which I suspect has to do with the altered hardware compared to 900. In a nutshell apart from windows which i havent tried, if you want your eee 901 to work YOU ARE STUCK WITH XANDROS OS, as nothing else really works. I tried in vain even to enable Advanced desktop mode in xandros but noooo. Each way offered to do so, caused different problems, like lost programs, lost tray icons, destroying aytorun options when you plug usb memory units and so on. 

I also tried ubuntu-eee which although misleads users by offering full 901 support. Beware as this is not the case. To be more exact you migh install it on your eee (aka copy it to the harddrive) but be sure that nothing will actually work, meanng: ethernet and wifi, camera,bluetooth, cpu scaling, double microphone, multitouch, FN buttons, and so on. Actually a full scale disaster if you want my opinion.

I wonder if this is the success of the special ubuntu version for the eee what kind of success will the regular ubuntu have.


Now, my questions are: Should I expect support in the near future for the Eee's 901 strange hardware or not?

Is there any suggestion to a distro which actually works?

Do you think that injection capable drivers will be available for this dreaded network card?


Finally: I was thinking os setting up the 901 as best as possible (adam custom kernel so wifi at least is solved) and swapping my 901 for mom's 900 as I basicly wanted it for network security tests so at last i can inject. Does this sound like a good idea, or 901 is way  better in some  aspects?

Ideas?

---

### Post by hamishaus on 2008-10-09
Hi DrSasaroli68

I don't think I could agree less! I have a 901 and I have had Ubuntu-Eee 8.04.1 running on it quite happily for a couple of weeks now (only got the 901 a month ago). All I had to do was download, transfer the ISO to a USB key, boot, install and EVERYTHING worked.

You need to get and run these ACPI scripts from here: [http://forum.eeeuser.com/viewtopic.php?id=39341](http://forum.eeeuser.com/viewtopic.php?id=39341). Then the buttons on the top work for Screen Off/On, BT Off/On, CPU % changing, Webcam Off/On. That's it! Nothing else req'd!

To fix screensaver not accepting password issue:
sudo chown root:shadow /sbin/unix_chkpwd
sudo chmod 2755 /sbin/unix_chkpwd

HTH
Hamish

---

### Post by michaelkahl on 2008-10-09
900 owner here...but I've heard from many 901 owners on this forum and others who have had great success with Ubuntu Eee 8.04.1 just like hamishaus described.  
Can you fill us in on some details.  Everything from where did you get your iso image file to how you installed it.  Just seems odd that so many things didn't work for you.
The 901's hardware is starting to become more standard, it's the new kid on the block and is built for netbooks.  Battery life is top notch on the Atom netbooks.  Support will get better for this hardware, that shouldn't be something to worry about.
Good luck with it.

---

### Post by KamakazieX on 2008-10-21
Ah, i should of hit up the forums before buying mine... anyways, the thing I did NOT like about ubuntu-eee is that it's not a true branch project by Canonical, therefore- unsupported, possibly unstable? This also .. "favors the best software available instead of open source alternatives (ie. Skype instead of Ekiga)" .. great n all but can that please be an optional package after post-installation?

---

