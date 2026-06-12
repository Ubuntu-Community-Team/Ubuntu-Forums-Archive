---
title: "CANON ImageRunner Advance C5045 printer driver"
date: 2011-08-21
forum: Hardware
---

### Post by fjkum on 2011-08-21
Hi,

Anyone here has luck installing and configuring this printer model?

---

### Post by cyiucsy on 2011-09-08
Yes, I managed to extract the PPD file from its Mac driver found on Canon's official site.
I downloaded this driver:
[http://downloads.canon.com/isg_public/CanonPPD_v3.05.zip](http://downloads.canon.com/isg_public/CanonPPD_v3.05.zip)
extract it, you will find a .dmg file
then use "dmg2img" to convert it into a .img file
(if you don't have it, run "sudo apt-get install dmg2img")
you might want to follow the instructions here:
[https://help.ubuntu.com/community/ManageDiscImages#DMG_Images](https://help.ubuntu.com/community/ManageDiscImages#DMG_Images)
then mount it and browse the mount folder
you will see a folder "us_eng", enter and you will see folders "MacOS9" and "MacOSX"
choose "MacOS9" and then you will see a series of folders, find the one named "iR-ADV C5045_5051"
there you go, the two PPD files are inside this "iR-ADV C5045_5051" folder.
copy them out.

then you can go to System -> Administration -> printing and set it up, when asked for drivers, choose "Provide PPD file" and use one of the copied PPD files (i used "CNADVC5045U1.PPD").

Good luck.

---

### Post by cyiucsy on 2011-09-08
by the way, you might want to change the paper-size first before setting up the printer. I cannot change it in GUI after setting up the driver, otherwise the C5045 printer will give you errors.

open a terminal (Ctrl+Alt+T)
type:
"gksudo gedit /etc/papersize"
delete the word "letter" inside and type "a4" (assuming you prefer a4 printouts)
save it and then do the printer setup.

Even after this, you might see "US letter" as paper size in the GUI but it's ok, I got mine C5045 working with a4.

---

### Post by cyiucsy on 2012-02-16
recently I have found that there's an easier way of installing that.
guess it might not interest you but it might be useful for someone else. so let me write that down here as well.

go to [http://software.canon-europe.com/products/0010766.asp](http://software.canon-europe.com/products/0010766.asp)
and choose Linux, English
then use the download the "CQue 2.0.2 Linux Driver DEB"
then install this package
and after that you'd be able to find it under "Choose Driver: Select printer from database" if you go to System->Administration->Printing and Add a new printer there.

---

### Post by pillarsdotnet on 2012-03-25
Installed the CQue 2.0.2 driver but cannot get the printer to print.

Tried:
[LIST]
[*]LPD(tcp/515) queue "lp"
[*]LPD(tcp/515) queue "print"
[*]Jetdirect(tcp/9100)
[/LIST]

In each case, went to: [LIST]
[*] Maintenance [LIST]
[*]Set Default Options [LIST]
[*]Canon Device Specific [LIST]
[*]Destination: Printer
[*]Mailbox: None
[*]User Password: Custom
[*]User ID: Custom
[*]Secured Password: None
[/LIST]
[/LIST]
[/LIST]
[/LIST]

And of course supplied my correct four-digit password and ID.

However, each time I print, the printer logs the attempt as ID='----' and status='NG' which I assume means "No Good" because the user id did not send.

(sigh) And since CanonUSA does not supply Linux drivers, I assume that to get support I must pretend I'm living in England.

---

### Post by cyiucsy on 2012-03-30
Well, I also use LPD but I am using Queue PASSTHRU.

Since you mentioned something about JetDirect, I wonder if you forgot to set explicitly the 'Make and Model' in the 'Printer Properties' window. My Ubuntu also discovered the printer and recognized it as a HP JetDirect by defult.

So after installing the CQue driver, the iR-ADV C5045/5051 option should be available in 'Choose Driver'(the 'Change' button next to 'Make and Model') -> 'Select printer from database' -> 'Canon'.

After this, it should read 'Canon iR-ADV C5045/5051' in the 'Make and Model' field in the Printer Properties window.

And about the support... I never called/mailed them so I really don't know but as a Linux user, somehow I'm a bit pessimistic to customer services. (sigh)

---

