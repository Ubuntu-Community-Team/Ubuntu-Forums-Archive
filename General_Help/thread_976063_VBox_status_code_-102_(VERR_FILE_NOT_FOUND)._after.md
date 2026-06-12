---
title: "VBox status code: -102 (VERR_FILE_NOT_FOUND). after Intrepid Upgrade"
date: 2008-11-08
forum: General Help
---

### Post by larrikin71 on 2008-11-08
I am running virtual Box 2.0.4_OSE on a recently upgraded Ubuntu machine. (now running 8.10 was previously 8.04). Now with hardy everything ran fine with my Virtual Windows XP installed but as soon as i had finished upgrading to Intrepid i get the following error message when i try and access my Virtual installation :


PIIX3 cannot attach drive to the Secondary Master.
VBox status code: -102 (VERR_FILE_NOT_FOUND).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}


Any ideas?
or do i need to start over?

---

### Post by larrikin71 on 2008-11-09
K...Looks like i have solved the issue...i unmounted the cd/dvd drive then remounted it and all is good..

---

