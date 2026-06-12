---
title: "Advice on hardware to run Ubuntu 64bit with Virtualbox Windows 7  64 bit guest"
date: 2010-04-10
forum: Hardware
---

### Post by VirtualUser on 2010-04-10
I'm going to build a new box that will boot in Ubuntu 64bit.  But there are a  few applications that I will still need to run in Windows, so I will run  a Virtualbox guest Windows 7 64bit on the system to handle those. 

I will also use the system to run Stata MP to analyze large datasets.  (Details of that package if you are interested:  [http://www.stata.com/statamp/](http://www.stata.com/statamp/)

I am particularly concerned about Ubuntu compatibility and the virtualization working correctly using Virtualbox ([http://www.virtualbox.org/](http://www.virtualbox.org/)).  

I have created specs for 2 systems with almost identical pricing and  am curious on thoughts to go one way or another, and also any  recommendations for substitutions. 

System 1 (P55) 
------------------- 
Asus® P7P55D-E  
Intel® Core™ i7-860  
NVIDIA® GeForce™ GTS 250 512MB GDDR3 w/ PhysX 
8GB Kingston HyperX Dual-Channel DDR3-1333MHz Low Latency 
1.0TB Western Digital Caviar Black SATA 7200rpm 32MB Cache 

System 2 (X58) 
------------------- 
Gigabyte® X58 (GA-X58A-UD3R)  
Intel® Core® i7-930  
NVIDIA® GeForce™ GTS 250 512MB GDDR3 w/ PhysX 
6GB Kingston HyperX Triple-Channel DDR3-1600MHz Low Latency  
1.0TB Western Digital Caviar Black SATA 7200rpm 32MB Cache 

Would you go with System 1 or System 2 for the purposes I am planning?   Any compatibility issues you can think of with Ubuntu 64bit host and Windows 7  64-bit Guest running under Virtualbox? 

I appreciate your thoughts!

---

### Post by rtilson on 2010-04-11
I run win7 64-bit guest with 10.04 host on my laptop with 4gig ram and a core 2 duo. Everything works fine and havent had any problems with. it Although I use Vmware Player, to me gives a little better performance over virtualbox. 

To me your system choices should work quite well for virtualization. If you are really concerned with virtual performance you can look into a motherboard that supports intel vt-d.

---

### Post by VirtualUser on 2010-04-11
That is good news.  Is that VMPlayer that you use the free of charge one?  Or the one that you must pay for?

Thank you for your help.

---

### Post by rtilson on 2010-04-11
VMware is free of charge, although you have to register with VMware before you can download. But they dont spam you with unwanted emails.

---

### Post by VirtualUser on 2010-04-11
Very helpful.  Thank you!

---

