---
title: "Printing Paper Size --- Error Letter instead of A4"
date: 2008-10-22
forum: General Help
---

### Post by Zymonick on 2008-10-22
Dear All,

when installing my computer I chose US environment and now logically CUPS always wants to print in the american "letter" format.

So I have done some searching in the web and amended the following changes: 

In /etc/papersize I added the entry A4.
I set the environment variable LC_PAPER="en_GB.UTF-8". 

And I changed in about:config of Firefox the variable print.postscript.paper_size = "A4". 

Nevertheless, when printing CUPS still sends the stuff in letter, which blocks our network printer until someone cancels the job. 

Could please anyone tell me what else I could try or is this a bug?

Thanks

---

### Post by KOld Iron on 2008-10-22
Have you tried to change the paper default size in:

Menu: System/Administration/Printing
Select your printer
Select printer options tab
Select paper size and change it to A4

I also have US environment, but living in Germany I use of course A4 and that configuration did it for me.

---

### Post by Zymonick on 2008-10-23
Thanks for your reply. Sure, the GUI was the first thing I tried. And it worked fine for printing the test page. However it didn't influence the printing behavior in any program. 

I even changed to UK environment by now, but it still wants to print in 'letter' format.

---

### Post by stinger30au on 2008-10-23
aaaahahhh yeeessss.... i do remember having this same problem once upon a time myself.... 

damn, but i can not for the life of me remember, once again my memory ha let me down, but it was very simple though...

damn it!!!!


after you changed the settings to A4 have you restarted the pc... i remember i had to restart the pc as well when playing with printer settings to get it right


sorry im not much help right now :-(

---

