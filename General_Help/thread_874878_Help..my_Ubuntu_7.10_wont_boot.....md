---
title: "Help..my Ubuntu 7.10 wont boot...."
date: 2008-07-30
forum: General Help
---

### Post by dreaswar on 2008-07-30
:(  :( :( 

Hi guys.. 
I have a Intel Core2 Duo E4400, 2Ghz, Intel DG965RY MB, 1 GB RAM ( in two 512 MB DIMM),Nvidia Geforce 8500 GT card( 512 Mb RAM), 2 SATA hard drives - one 160 GB and other 250 GB.

Window Xp is installed on the 1st and Ubuntu on the 2nd. 

I have been dual booting for the past one year. 

i had to reinstall my Windows,then i could reinstall grub and get dual boot working again. It was all fine

My current problem is that i cannot boot into Ubuntu. It happened all of a sudden and nothing has crashed, no power surges... unclean shutdown..etc..  but i can boot into Windows XP from Grub.

Grub loads... two kernels are listed, their recovery modes, Memtest and the XP are listed. 

When i boot into any kernel, the Ubuntu progress bar comes and then gets stuck... or if i hit the Ctrl+Alt+F1 to go to Verbose mode the screen goes black with a blinking cursor at the top corner. 

Recovery mode ... number keep scrolling by and never seem to end...... i waited for 1 hour and then shut it down again. 

Memtest doesnt work.. it yields this error..  "Error 28: Selected item cannot fit into memory"

Then i tried Live cds. It also did'nt boot.. Progress bar got stuck at the same place that Ubuntu gets stuck while booting.

In all this i thought it was a RAM problem and tried reinserting them in to their slots .. this seemed to have solved it for a day and then reappeared next day...

XP boots fine... so is something else wrong?? :confused:

what can i do ?

Please help....

Sorry for the long post.. i thought i will tell my story in one shot...

Thanks..

---

### Post by dreaswar on 2008-08-04
k guys. 

seemed to have solved it.. 

part of it solved by itself and made it easier for me. 

suddenly the recovery mode started to work and so did the live cd. 

so i tried booting with the recovery mode. 

i did sudo apt-get update and upgrade, aptitude update and distribution upgrade. 

i had to do a reconfiguring of the X server and then its all right now.

Still the Memtest does'nt work though.

i still get the Error:28 selected item too big to fit
into Memory.

---

