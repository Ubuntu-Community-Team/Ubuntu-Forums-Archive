---
title: "HPLIP Problems"
date: 2008-09-24
forum: General Help
---

### Post by zambiandreams on 2008-09-24
I have an HP 1020 Laserjet printer, and am currently trying to get it working.  I am running 8.04.  

Every source so far as suggested I install hplip and then run 'sudo hp-setup.'  However, as soon as I run this command, I'm given the error "CUPSEXT could not be loaded. Please check HPLIP installation."  I reinstalled all the hplip packages I could through synaptic, but still get the same error.  What is CUPSEXT and how can I get this blasted printer working?

---

### Post by zambiandreams on 2008-09-25
OK, I figured it out!  In order to get this HP 1020 Laserjet to work, I first downloaded hplip from the HP site, which is version 2.8.9.  I reinstalled hplip in full, and then plugged in the printer and powered it on.

From the terminal I ran 'hp-setup,' which installed the printer.  However, after that stage any job I sent to the printer would show up in the print queue but never print; the job was always listed as 'processing.'  

I went back to the terminal and ran 'hp-check' which showed everything was fine except I was told 'error: SIP not installed or version not found.'

I went to synaptic, typed in 'SIP' and found a package called sip4, which is described as 'Python/C++ Binding Generator.'  I installed said package and then ran 'hp-check' again in the terminal.  It still gave me the 'SIP not installed' error, but I tried printing a test page and it worked.

If the printer stops working later I will be back on here, but for now I hope this works for anyone else who needs it.

---

### Post by robertyou on 2008-11-10
Well, I had a different problem on my machine. Just thought I should post something here for reference.

After hplip was installed, I started hp-toolbox to configure my printer (hp LaserJet 1020). However, the required plug-in wasn't installed correctly after the set-up. The printer's status stays as "idle" and wouldn't print anything. Checked with "hp-check" and it returned 1 error "Required plug-in status: Not installed".

In the end I just downloaded latest version of hplip ([http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)) and installed it from terminal. It works like a charm now.

---

### Post by zambiandreams on 2008-11-10
Well, I had this printer working for a while, but am now stuck again after updating to Ibex. 

The HP Device Manager continually lists the printer as 'busy,' even when i have canceled all the print jobs and even powered off and then re-powered on the printer.  

I ran hp-check and was told 'error: SIP not installed or version not found' even though I installed sip4 through synaptic.

I went so far as to reinstall all the hplip packages I could find in synaptic, but still am given the same error.

---

### Post by editrix on 2008-11-10
Out of curiosity, I searched your error message "SIP not installed" on uboontu.com (last link in my sig) and it seems SIP has something to do with networking. I too had problems with printing (although not yours) because for some reason HPLIP seems to think my printer is networked, even when it isn't.

I had other problems related to networking and solved them by changing my /etc/hosts file. I don't know enough about your setup to recommend doing anything, except maybe go over those uboontu hits and see if you can figure it out for yourself. But it might have something to do with networking, even if you're not networked.

---

### Post by Mendokuse on 2008-12-12
hey just curious - I have a HP P1005 which used to work in hardy but not in Intrepid. Anybody managed to get their HP printers working in Intrepid so far?

---

