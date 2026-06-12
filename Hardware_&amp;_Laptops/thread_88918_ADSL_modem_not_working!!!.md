---
title: "ADSL modem not working!!!"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by gatt143x on 2005-11-11
I have a Adsl modem.. GS7070 chipset.. XAVI Xentrix X7005Q.

I get the following error while exectuing "eciadsl -start"

[3/5] Synchronization...
can't set interface 0 to alt setting 4

synchronization failed.  :( 

(during the process, the Link/Data LED never glowed.. The Power LED is on through out.. right from when my PC is switched ON.. In step 2, it reported firmware successfully uploaded)..

Found out d Vid1/Pid1 and Vid2/Pid2 manually for my modem... They are 0915/8101 and 0915/8101.

VPI is 1 and VCI is 32. As none of the synch files provided in the package worked, I created my own in windows xp.. using USB Snoop tool from eciadsl website.. Then in ubuntu converted the USBsnoop log file into my_synch.bin file and put it in eciadsl directory.. I've configured eciadsl to use my_synch.bin and provided other details required.

Can anyone explain why the above stated error occurs and a probably solution??  :confused: 

Plz helppppppp me on my verge to throw away Micros*it WinXP once n for all n experience d power of ubuntu..!!!  :KS 

-Gatt

---

### Post by 23meg on 2005-11-11
There must be an "alt setting" variable somewhere in your config files; I don't remember where since I used eciadsl's GUI config tool to set it; try setting it to another value such as 5. You should be able to find what to set this to if you read the eciadsl documentation.

---

### Post by gatt143x on 2005-11-12
Hi!

Thanks for your reply. I checked for it in the documentation. Then I realised I had the 0.10 version of eciadsl while the latest is 0.11. So, downloaded the same and installed it. 

Now my modem get synched!!!!!!!!!(Yay!!). Almost there.. But it gets timed out in the next step [4/5] Connecting to provider...

The default one is VCM_RFC was giving this problem. So, I contacted my Service Provider (Airtel). They said that the mode is LLC_RFC2516. But in eciadsl, I don't see it in the probable listed modes.

What do I do now???? Plz HELP!!!!!!!!!!!!!!!! It jus feels like the internet in Ubuntu is just in front of my eyes.. I just need 2 establish a connection to the provider!! How!!!!

---

