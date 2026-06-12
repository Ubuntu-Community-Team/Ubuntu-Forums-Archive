---
title: "Problems with Printer"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by Rodrigo on 2005-05-02
I installed the my printer on Kubuntu with no problems, I even made a small HOW TO...
So I install the same printer on UBUNTU... make the install, and print the test page perfectly, The problem is that when I try to print from OpenOffice IT starts to print from the HALF of the PAGE!, and I have to end the printing jobs manually  :mad: , (I check the size of the pages, so thats not the problem), I like ubuntu the most, I dont want to return to kubuntu. What could be the problem?  :?  :?  :?

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=Rodrigo]I installed the my printer on Kubuntu with no problems, I even made a small HOW TO...
So I install the same printer on UBUNTU... make the install, and print the test page perfectly, The problem is that when I try to print from OpenOffice IT starts to print from the HALF of the PAGE!, and I have to end the printing jobs manually  :mad: , (I check the size of the pages, so thats not the problem), I like ubuntu the most, I dont want to return to kubuntu. What could be the problem?  :?  :?  :?[/QUOTE]
 It'd help if you at least mentioned your printer model and the driver used for it (from System-Administtation-Printing tool). Also: did you try printing to this printer from OpenOffice in Kubuntu?

---

### Post by Rodrigo on 2005-05-03
[QUOTE=Alexander Kirillov]It'd help if you at least mentioned your printer model and the driver used for it (from System-Administtation-Printing tool). Also: did you try printing to this printer from OpenOffice in Kubuntu?[/QUOTE]

Canon i250, and the driver is i250 ver 2.3 (which IS NOT in the system admin printing tool), and YES! I printed OpenOffice docs in Kubuntu...  :?

---

### Post by Rodrigo on 2005-05-05
well, any help?...  :neutral:

---

### Post by DutchLau on 2005-05-05
I know it's not much advice, but get a HP printer. Most nowadays have full linux support because of the HP-linux project.

If you ever decide to get an HP printer I'm happy to help, but because I don't have a Cannon (which has horrible linux support I believe - like ATI) I can't help you out.

Sorry mate,

DutchLau

---

### Post by Rodrigo on 2005-05-05
[QUOTE=DutchLau]I know it's not much advice, but get a HP printer. Most nowadays have full linux support because of the HP-linux project.

If you ever decide to get an HP printer I'm happy to help, but because I don't have a Cannon (which has horrible linux support I believe - like ATI) I can't help you out.
[/QUOTE]

the last thing I want to do its change my printer (dont have $$$ hehe), and I cant belive that the same printer did work on Kubuntuand doesnt want to work properly on Ubuntu! :S:S:S

but thanks for the "tip" hehe.

---

### Post by DutchLau on 2005-05-05
@ Rodrigo,

I might have though about something that will work for you. Try the following:

I've just installed my HP 5150C Deskjet with Ubuntu. It seems to work well - but only AFTER I got the official drivers installed from HP. Perhaps this has something to do with the printer driver not being supported by cups. I'm an uber noob with Linux so I've warned you. If you inflict any damage upon your PC it's not my fault!

Now go to [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi) Download the .PPD file for YOUR printer. (Put in your printer manufacturer and model number and then press "show" to the left of it. Now it will go to the next page and you can press download PPD)

Now we'll go to Gnome and we'll set up your printer. Go to System => Administration => Printing. Add a New printer, follow the steps (Use detected printer) Choose the model, Press "Install Driver" and find the .PPD file you saved.

This should successfully install the printer. Restart cups, or reboot the computer, either works.

Let us know if it worked!

Cheers,

DutchLau

---

### Post by Rodrigo on 2005-05-06
Well DutchLau, Thanks again  :grin: , but the my printer (Canon-i250) its NOT in linuxprinting.org, belive me I search there when I had kubuntu, I dont have the official Canon drivers, but I found ones that work in KUbuntu, I use the same drivers in the same machine but this time with ubuntu on it, and the crap prints the test page ok, but print from OpenOffice or gEdit .... Ohhhh dear.... the thing prints from HALF!!! the page  :? :?, and the printer jobs just freezes...
I found some one with the last same problem:
[http://www.ubuntuforums.org/showthread.php?t=30410](http://www.ubuntuforums.org/showthread.php?t=30410)
but... I dont think this is the "right" answer  :-P, but I'll try it any way   :roll: 

and the other problem (the half printing problem), well... Im clue less :?


(and the mini how to install canon i250 in kubuntu is here: [http://www.ubuntuforums.org/showthread.php?t=29255&highlight=Canon+i250](http://www.ubuntuforums.org/showthread.php?t=29255&highlight=Canon+i250))

---

### Post by lorap on 2005-05-06
ahtung ahtung friends!
there's a way to solve this problematic bug.
rodrigo,you'll need to add your printer via cups printing services.
all derectives needed to proceed this procedure succesfully are explained at this site:

[http://www.cups.org/doc-1.1/sum.html](http://www.cups.org/doc-1.1/sum.html)

let me know if you succeded amigo.

---

### Post by Rodrigo on 2005-05-07
[QUOTE=lorap]ahtung ahtung friends!
there's a way to solve this problematic bug.
rodrigo,you'll need to add your printer via cups printing services.
all derectives needed to proceed this procedure succesfully are explained at this site:

[http://www.cups.org/doc-1.1/sum.html](http://www.cups.org/doc-1.1/sum.html)

let me know if you succeded amigo.[/QUOTE]

thaks for this reply, I will try it as fast as I can  :grin:

---

### Post by Rodrigo on 2005-05-10
ok, the manually cancel job problem is fixed, it was a configuration thing, but the other one havent gone, so, Im going back tu kubuntu, in one of my pcs only  :wink: 
thanks for your help

---

### Post by müller on 2005-09-12
Hi Rodrigo.
I have the same problem. From OO my i250 starts to print from half page down.
I checked the file->printer configuration and found that the paper format was on A5.
I changed it to A4 and...... it didn't work, actualy it changed back to A5. (i guess it's a bug.)
Then i started **oopadmin** and found out the margens are WRONG! 
I changed it and..... it didn't work. :( But i'm sure the problem is here at the margens.

---

### Post by müller on 2005-09-12
well now it works :)
but i'am not sure how i fixed it.
Here is the plan of what i did.
1. Deleted the printer from  System->admin->printers
2. Added the priter trough CUPS on [http://localhost:631](http://localhost:631)
3. started **oopadmin** and changed the paper format and the margens
4. (su) killall cupsd
5. (su) cupsd
....and it printed fine

---

### Post by Gray. on 2006-01-02
Sorry to bring up a dead topic but I have the problem of the jobs having to be manually cancelled and wondered how exactly you got rid of it.

---

