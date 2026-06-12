---
title: "internet not working in 12.04 LTS"
date: 2012-05-24
forum: Hardware
---

### Post by idom on 2012-05-24
Hi 

I have installed 12.04 LTS on my toshib z835  and I had used it for around 3 weeks without any problem however yesterday suddenly my internet has stopped working. 

Only change was my battery died while it was connected. How do I figure out what is wrong ? 
Can any body help me here?

Wired and wireless both are not working and I am able to ping to my wireless router as well my desktop connected to same wireless router via its IP

idom

---

### Post by idom on 2012-09-06
Can anybody help. 

I re installed the system again and it is working till now. 
Now suddenly it has stopped working 

And this time I have so much on my system I can not afford to reinstall. 

Please help.

this time even battery had not died it just stopped working without doing anything any suggestions.

I am able to ping things on the lan however not able to ping any website.

Please help

> **idom said:**
> Hi 

I have installed 12.04 LTS on my toshib z835  and I had used it for around 3 weeks without any problem however yesterday suddenly my internet has stopped working. 

Only change was my battery died while it was connected. How do I figure out what is wrong ? 
Can any body help me here?

Wired and wireless both are not working and I am able to ping to my wireless router as well my desktop connected to same wireless router via its IP

idom

---

### Post by lincoln32 on 2012-09-06
how are you connected to the internet wifi or lan or??

---

### Post by idom on 2012-09-06
> **lincoln32 said:**
> how are you connected to the internet wifi or lan or??

I tried both wifi and wired and both it is not working 
I can do all the experiments that you suggest. 


idom

---

### Post by lincoln32 on 2012-09-06
not my strong area but check the network drop down and verify a check mark by enable networking and enable wireless. also check for anything that is grayed out or labled diconnected

---

### Post by idom on 2012-09-06
> **lincoln32 said:**
> not my strong area but check the network drop down and verify a check mark by enable networking and enable wireless. also check for anything that is grayed out or labled diconnected

done all this booted also couple of times. I wanted to verify that nothing has gone wrong from the hardware side so booted with from USB ( 12.04.01) and checked that internet is working so hardware issues is ruled out. 
Is there anyway to check if some part of HDD is corrupted ? 

I have seen some warning that some sector is bad while shut down or boot up sometime ago. 

Please help I need to submit something by end of next week to client and without this wireless working I will die. 

idom

---

### Post by typhoon_tip on 2012-09-06
Check the smart data status under Disk Utility program (use Unity to find it), it will tell you the health of the HDD and if any bad sector. Post back the result here !

---

### Post by idom on 2012-09-06
> **typhoon_tip said:**
> Check the smart data status under Disk Utility program (use Unity to find it), it will tell you the health of the HDD and if any bad sector. Post back the result here !

Hi it is failing(read) the fast case Now I am running the extended test case ? 

Is there any log I have attached screen shot.

idom

---

### Post by lincoln32 on 2012-09-06
you have a bad drive that can not a section you might want to get a new drive in a portible case. that way you could install Ubuntu then put the old drive in the case and copy all the data over.
backup-ups or working copy of complete disks is a must have on any computer
with any operating system:rolleyes:

---

### Post by idom on 2012-09-06
> **lincoln32 said:**
> you have a bad drive that can not a section you might want to get a new drive in a portible case. that way you could install Ubuntu then put the old drive in the case and copy all the data over.
backup-ups or working copy of complete disks is a must have on any computer
with any operating system:rolleyes:

Hi 

I have all the critical data backed up. And as this is Toshiba ultrabook so I am not sure if I can buy a SSD myself and replace it.

I am just curious that if there are bad sectors how come only this internet function is getting affected ( this is the 2nd install of the Ubuntu 12.04 and and  both the times I have faced this same internet issue) 

also is there any way to confirm this? And what about other people ? 

Nikunder can you run the same  thing over your machine ?

---

### Post by typhoon_tip on 2012-09-06
> **idom said:**
> I am just curious that if there are bad sectors how come only this internet function is getting affected ( this is the 2nd install of the Ubuntu 12.04 and and  both the times I have faced this same internet issue)

Probably because of the cache, which is written/read over many times when you surf (browser load data from web into the cache, then read the disk to render the page).

---

### Post by idom on 2012-09-06
> **typhoon_tip said:**
> Probably because of the cache, which is written/read over many times when you surf (browser load data from web into the cache, then read the disk to render the page).

The machine is under warranty ? Will they replace the SSD do you have any idea?

Samarth

---

### Post by lincoln32 on 2012-09-06
operating files are normally do not get moved and end being located in the same location during install so same drive and same operating systen the same file will end up close or in the same location. in your case it is in a area that cannot be read but can be written to. the repair is the same a bad drive will always  give intermitant operation and usually gets worse fast.

---

### Post by typhoon_tip on 2012-09-06
> **idom said:**
> The machine is under warranty ? Will they replace the SSD do you have any idea?

Samarth

I hope so... :popcorn: How old is the computer ?

---

### Post by idom on 2012-09-06
> **typhoon_tip said:**
> I hope so... :popcorn: How old is the computer ?

I bought it less than 6 months ago !! 

idom

---

### Post by idom on 2012-09-22
> **idom said:**
> I bought it less than 6 months ago !! 

idom

I gave it to toshiba service centre and (as expected ) they said that they don't support ubuntu. They re installed windows 7 and now with chkdsk there are no bad drives

---

### Post by lincoln32 on 2012-09-22
bad spots in a drives can come and or go. while I would hate to trust a drive that failed once already. As far warr goes they will not want to replace anything unless they have to. I seldom use a warr for that reason
but we all hate to throw parts and money at new computer too. try it and hope it stays running. and keep a good back up just in case. :)

---

### Post by idom on 2012-09-22
> **lincoln32 said:**
> bad spots in a drives can come and or go. while I would hate to trust a drive that failed once already. As far warr goes they will not want to replace anything unless they have to. I seldom use a warr for that reason
but we all hate to throw parts and money at new computer too. try it and hope it stays running. and keep a good back up just in case. :)

Yeah I guess that is true. However it is SSD so I have slightly high hopes and I keep all data backup always 

thanks for your help.

---

