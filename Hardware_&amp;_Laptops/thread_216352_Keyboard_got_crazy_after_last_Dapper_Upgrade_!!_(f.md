---
title: "Keyboard got crazy after last Dapper Upgrade !! (fresh install works fine)"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by patrick295767 on 2006-07-15
Dapper Alternate  from fresh instllation : keyboard working ; 

Since last week, the keyboard is missing keys typed ... 
Like it's not totally and fully reacting.
  I press ALT F1 then get lots of windows Xterm
like ALT got blocked 
  
I have fvwm. So incompatibliyt with it ?;)   

apt-get upgrade  results in non workign keyboard;
  
Machine : toshiba laptop

---

### Post by patrick295767 on 2006-07-18
Other laptop : Compaq  : Same Problem
  
The Dapper Linux workstations keyboard is gone.
  
I reinstalled Breezy,  :it's working great under Breezy.
  
There is a serioous **issue** to be done there with : 

**login console & keyboard for laptops**
you can enter the login
but the password, you have to rush like crazy if you wanna login !! 
  
(I hope that the development team will be conscious that there is sthg wrong with lastly dapper update)
  
the dpkg -l of the laptops:
there :[http://patrick295767.sitesled.com/miniram/prob_linuxstation.txt](http://patrick295767.sitesled.com/miniram/prob_linuxstation.txt)
  
I can login in ssh to the dapper prob laptops to work on it
and the station is working normally.

So, ??

---

### Post by patrick295767 on 2006-07-19
I have found finally. 
That's a bug with plptools as written here: [http://www.ubuntuforums.org/showthread.php?t=187583&highlight=psion](http://www.ubuntuforums.org/showthread.php?t=187583&highlight=psion)

shitty to return to breezy
I liked dapper :-(

---

