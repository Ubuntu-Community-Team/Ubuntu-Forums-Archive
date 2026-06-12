---
title: "parallel port configuration problem lexmark Optra T612 in Ubuntu Feisty Fawn 7.04"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by ronny_d on 2007-07-26
Hi People, Please help me. I have on a Dell computer usb 1.1 Ubuntu Feisty Fawn 7.04 desktop a problem to configure my laserprinter Lexmark Optra T612; the printer itself works fine and prints out its own testpage perfectly, but not via my Ubuntu Feisty Fawn 7.04 desktop on this Dell computer usb 1.1 I click on 'system' and administrate then 'printers' and click on that and the tool 'gnome-cups-add' or something automatically appears and with 'step 1' it already starts, that is: i cannot choose the parallel port for my printer that i need but see instead that this computer has already reserved on parallel port #1 both Canon and Epson (i wonder why!), else i can choose LPT#1 (serial port is but no option because my printer is parallel 1 or 2, both, but i do not know how to configure else port 2 or so..., the option is not given as far as i can see). Anyway: i choose LPT#1 for example, the printerdriver Lexmark Optra T612 is given in the list so that seems to be no problem at all and i choose it, then anyway for sure my printer is not detected by my Ubuntu Feisty Fawn and anyway i choose option "standalone printer" so no 'network printer', but lateron after configuration... i check back and see that the printer configuration tool has set my printer automatically on 'networkprinter' and some 'serial port' which will never work; but when i make it stable at "standalone" printer / local printer or detected printer, it somehow cannot recognize the parallel port and says when i want to print via this software a testpage: 'parport busy', or something, or: 'will retry in 30 seconds' or something, or: 'unknown host'..., anyway: no testpage. So some is really wrong with the connection... and therefore the communication between computer and printer. I set my description of the printer at lp (first i had typed the description 'lpr', but that did not make any difference), and path is /dev/lp0; now when i with sudo want to add the group lp (because it is not there), i can add it, but moments later, when i but check, also after having rebooted for example..., and although i have administration right / permissions, my added group 'lp' is but no more there... It feels all like a mess. My printer is working, the light is on, the driver for my Lexmark Optra T612  is in Ubuntu Feisty Fawn 7.04, but something is wrong with the parallel port connection. How to solve this apparent printer parallel port problem? Who o who can help me solve this problem please..., and help me have my printer connected to my computer and vice versa? Someone outthere..., geeky enough, please help.

---

### Post by ronny_d on 2007-07-27
Hi People, 

You know: the parallel port just must be broken and that is the cause, else i can find no reason why the named printer was not installed immediately, its driver being in the list and all LPT#1 there. 


So what have i done? I went out to get myself some coffee (spilled all beans here...).


;-)

---

