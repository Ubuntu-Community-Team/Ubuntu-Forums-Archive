---
title: "Documents Won't Print"
date: 2008-09-08
forum: General Help
---

### Post by balahh on 2008-09-08
Neither AbiWord nor OpenOffice would print my documents for some strange reason. Every time I try to print it, what comes out is a bunch of weird characters like the ones you would see when you use the font Wingdings. Can anyone help me with this problem? Thanks :)

---

### Post by bmac on 2008-09-08
Some additional information may be beneficial.

1. Can you print correctly from any other program?
2. What type printer are you using?
3. Have you checked your printer preferences in both OO & AbiWord?

Others may have addition questions, so please post as much information as possible...

---

### Post by balahh on 2008-09-09
1. I haven't tried printing using Notepad or something because they are inconvenient to use when trying to type an academic paper or a script. That's why I'm determined to find a solution for AbiWord or OO. :)

2. My printer is an hp deskjet 845c

3. Yes I have checked and re-checked but I just cannot figure out what is wrong. I know it isn't the printer's problem because it can print from my laptop which uses a Windows OS/ MS Word. It is a hassle to have to transfer my document to the laptop to print when there could be a possibility of it being printed from the PC.

Again thanks to any future replies :KS

---

### Post by bmac on 2008-09-09
Without knowing if your printer works with any other program, The only solution that I believe might work is by installing the HPLIP driver from this site. I suggest using the HP installer. 
I checked and your printer is supported. I do recall a similar experience with my HP 712C but it won't print at all from Firefox. After installing this driver the problem was resolved.

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

Hope this helps.....

---

### Post by balahh on 2008-09-10
Please forgive me for this noob question but, how do you install this? :lolflag:

---

### Post by bmac on 2008-09-10
I simply went to the "installer walk through page" and followed the instructions. I experienced no problems and my printer was up and running in minutes...

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5761112](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5761112)


Hope this helps....

---

### Post by balahh on 2008-09-11
Gah, it didn't work. :( OO and Abi still won't print but at least now the printer responds, i.e., it "prints" (as in it goes through the printing process) but there is nothing that comes out on the paper. It can't be my ink because it's new. :confused:Any suggestions?

---

### Post by bmac on 2008-09-11
Hopefully you rebooted - I had to.

One thing that might help is to identify if your printer is printing properly to eliminate that aspect and narrow the issue to the word processors.

After installing the new print driver and HP icon should have appeared in your panel. If you right click on the icon and select "HP Device Manager" it should open a window that shows your printer on the left side. Under the actions tab left click on test page and see if your printer prints a test page. Also check the status of your printer under the status tab - when not printing it should show a green led next to the word Idle.
Or go to system/administration/printing/
Select your printer from the left side and under the settings tab left click on test page. You may also wish to check the other tabs to assure the setting are correct.

If it prints a test page, I really think it would help if you would print something from a different program, just to identify that the issue specific to you word processors. 

Good Luck...

---

### Post by balahh on 2008-09-12
Unfortunately, it still does not work. I was thinking of re-installing the program coz maybe I missed an error during installation. Now my problem is how do you uninstall the program? :lolflag:

---

### Post by bmac on 2008-09-12
This should help....

[http://hplip.sourceforge.net/howtos/uninstall.html](http://hplip.sourceforge.net/howtos/uninstall.html)

---

### Post by balahh on 2008-09-13
"|error: Printer queue setup failed. Please restart CUPS and try again."

What does that mean? :confused:

---

### Post by bmac on 2008-09-13
It appears to have failed to setup a print queue. Don't know why. 
Hopefully, someone will assist that has more knowledge regarding this issue....

Bump....

---

### Post by balahh on 2008-09-13
Bump

Could anyone please help me with this problem? :)

---

### Post by balahh on 2008-09-15
Anyone? 

bump

---

### Post by balahh on 2008-09-16
BUMP! :cry:

---

