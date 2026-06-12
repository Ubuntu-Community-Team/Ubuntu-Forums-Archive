---
title: "installation issues"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by nutsorters on 2009-08-30
After suffering constant issues with XP, I decided to try Ubuntu.  I downloaded the live CD, burnt it and successfully ran Ubuntu from the CD.  I then backed up my files, removed the master HD and replaced it with a brand new one.
 
I then set about installing Ubuntu.  I have tried installing Ubuntu i386 and 64bit versions, and also Kubuntu i386 and 64bit.  None work.  Sometimes I get error messages, other times it just hangs.  Sometimes the live CD boots, other times not.
 
I have read through all the help files and tried burning the CD several times at low speed.  Tried changing BIOS settings.  I tried swapping my DVD drives over and using a different one - nothing seems to make any difference.
 
Is there anything else I could try?  The latest attempt resulted in getting as far as clicking the 'install' button, only to see the 'Partitions formatting' window freeze at 5% and the CAPS LOCK light flashing on and off!
 
Thanks
 
 
Setup:
Abit KV8 Pro (socket 754) with Althon XP 64bit 2GHz CPU
2Gb RAM

---

### Post by PorkyPie on 2009-08-30
If you use Jaunty, you should read these release notes, [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904) , for problems that may effect you.

Secondly, did you try to re-download ubuntu? If you did, try downloading a previous version like Intrepid Ibex.

Hope this helps

---

### Post by nutsorters on 2009-08-30
Thanks for the reply.
 
Just checked the link in your post and don't think any of those issues affect me.
 
I have tried downloading several times, using both torrents and direct download.  I have checked thte checksum and all seems fine with the iso...

---

### Post by sandy4linux on 2009-08-30
Setup:
Abit KV8 Pro (socket 754) with Althon XP 64bit 2GHz CPU
2Gb RAM[/quote]

hi,
I think this sys configuration is excellent. Since you have installed new hard disk.  Click radio button, entire hard disk,  when the partition window pops up. Sometime partition format screws up the installation. By selecting this option you may have only 1 partition. But this may help you to get it installed. 

 (When you install back to back with the default partition option, that leads to generate many sda partitions, so avoid using it..that might have screwed your hard disk already)

If you would like to have more than one partitions , then you have to undergo many procedures,
I will explain, if you really need it..

I hope this may help you..

Welcome to Linux
Regards,

---

### Post by nutsorters on 2009-08-30
Sandy,
 
Thanks for the reply.  I have been trying to install to the entire drive - I have a seperate physical drive so don't need to partition.
 
I had the same installations problems yesterday and assumed it was a hardware issue.  I bought a new hard drive but still getting the same problems.
 
Is there anything else I can try or am I best reverting to XP?
 
Thanks again

---

### Post by sandy4linux on 2009-08-30
In order to work Ubuntu it must have enough space for root,home and swap.(

Root(\)
So pls try partition manually, 

 right click on Unmounted partition and click new,
 
memory space should be minimum 4 gb or more( suggest 10 gb, its good for future)

format-ext4
select ' \' in the option below ----- for Root
 click ok

now repeat the procedure for swap partition

 right click on Unmounted partition and click new,

format-swap

select ' swap' in the option below ----- for swap
 click ok

now repeat the procedure for  home partition

 right click on Unmounted partition and click new,
 

select ' home' in the option below ----- for Home(this is your main partition)
 

memory space  is your remaining partition
format-ext4
click ok

hope this may help you..

regards,

---

