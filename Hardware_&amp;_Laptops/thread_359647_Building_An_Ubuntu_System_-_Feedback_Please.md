---
title: "Building An Ubuntu System - Feedback Please"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by zero-9376 on 2007-02-12
Hi all,

I am hoping to get feedback on building the following system:

CPU: Core 2 E6400 - 2.13GHz (no further details needed)
MOTHERBOARD: ASUS P5N32-E SLI (nvidia 680i chipset
[http://au.asus.com/products.aspx?l1=3&l2=11&l3=397&model=1459&modelmenu=2]("http://au.asus.com/products.aspx?l1=3&l2=11&l3=397&model=1459&modelmenu=2")
GPU: ASUS Silent 7600gt 
RAM: 2gb g.skill ddr-800
HDD: Random assortment 320s-80s

My biggest concern is the motherboard, i want something that is going to work out of the box,  i dont know if ill be using a raid setup or not yet. If you have experience with this board and ubuntu please provide feedback as i haven't been able to find anything specific to the P5N32**-E**. 

Im using the passive card because ive had bad luck with fans on previous cards and live in a townsville australia (its hot here) so lost the cards. I would like to know if the card will be ok to run two screens (hopefully with aiglx) one at 1650x1050 and the other 1280x1024.

I plan on using this system for a long time and have been saving for some time to get it so any advice will be greatly appreciated. I plan on using dapper at the moment but will move to feisty when its released as i want to run a range of virtual machines for testing and engineering applications and would prefer to do so without vmware. 

   Thanks in advance.

---

### Post by zero-9376 on 2007-02-12
i have seen signatures indicating people are running this board, can someone confirm its operation under ubuntu.

---

### Post by tommcd on 2007-02-13
If you are looking for a core-2-duo compatible motherboard, you may want to consider the Asus P5B series. The Phoronix people found the Asus P5B deluxe to work well:
[http://www.phoronix.com/scan.php?page=article&item=621&num=1](http://www.phoronix.com/scan.php?page=article&item=621&num=1)
You may want to check out the phoronix forums also. The nvidia 680i chipset is pretty new. I would be interested to know if ubuntu would run on it.

---

### Post by Benitez on 2007-02-13
[SIZE="3"]If you want to build your own computer, please ignore this post.

Otherwise, take a look at the systems that this computer company, [System76]("http://www.system76.com") makes. They are located here in US, and their systems seem to be fully Ubuntu compliant (I assume they test them).

P.S.: I do not work for them; I am planning to get one of their desktops soon (for my mom).[/SIZE]

---

### Post by zero-9376 on 2007-02-13
I looked at the P5B sereies but also found posts about the jmicron ide controller not being properly supported. Also I want the 6 sata ports and for future 3 graphics card (2 in sli + 2 other monitors running fromm 3rd card). As I said I have seen signatures with people using these boards, there also seems to be implied information that they work with with the exception of the networking which requires a modification to modprobe.conf. I just need someone using ubuntu to confirm this.

Thanks for the replies.

---

### Post by tchoklat on 2007-02-13
Greetings fellow Oz Ubunter. I am in the Hunter Valley of NSW and putting a system together.

I am looking at a Gigabyte GA55-SLI-S4 card with a SATA 11 drive. Any thoughts on this set up?

I looked at the site referred to above in the US though M/Bs are not mentioned!

Tony

---

### Post by zero-9376 on 2007-02-13
I can only assume that you have miss-typed the model name of the motherboard as I can't find anything on Google or staticice. What chipset does the board use?

---

### Post by tchoklat on 2007-02-13
[http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2442&ProductName=GA-M55SLI-S4](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2442&ProductName=GA-M55SLI-S4)

uses [B]NVIDIA® nForce 590 SLI chipset


tony (forgot the 'M' sorry
[/B]

---

### Post by zero-9376 on 2007-02-13
Looks like its all good if you look at these threads:

[http://ubuntuforums.org/showthread.php?p=1504441](http://ubuntuforums.org/showthread.php?p=1504441)

[http://www.ubuntuforums.org/showthread.php?t=224416](http://www.ubuntuforums.org/showthread.php?t=224416)

No-one willing to tell me about the asus 680i board?

---

### Post by tchoklat on 2007-02-14
thanks for that - you are geting no takers though!
 
 
regards and thanks
 
Tony

---

### Post by tchoklat on 2007-02-14
try this mate
 
[http://techgage.com/article/asus_p5n-e_sli](http://techgage.com/article/asus_p5n-e_sli)
 
 
ozy ozy ozy
 
 
found on the tuxmachines.org site so should be linux compatible!

---

### Post by zero-9376 on 2007-02-14
appears so...glad to have been of service

can someone please help me out now?

---

### Post by tchoklat on 2007-02-15
this link relates to the mobo that you are looking at doesn't it?

---

### Post by zero-9376 on 2007-02-16
no the link is about the p5n not p5n32, which uses the 680i chipset rather than the 650i, thanks though.

---

