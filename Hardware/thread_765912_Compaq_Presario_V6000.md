---
title: "Compaq Presario V6000"
date: 2008-04-24
forum: Hardware
---

### Post by rob3r on 2008-04-24
Attempting to install 8.04 on a friends Compaq Presario v6000. I tried doing this with 7.10, ran into wireless issues and gave up because my friend was in the middle of the school year and needed the machine badly.

So, I have now downloaded both the 8.04 64bit and 32bit desktop ISOs. I booted into the live environment with the 64 bit cd no problem, but the wireless wasn't detected.

I have searched the forums and found a lot of info on this laptop, but it was for 6.06 and 6.10. Just wondering if anyone has had any luck with 8.04 with this computer, and what it required to get going. 

Any help is greatly appreciated, I would really like to get my friend going with a great Ubuntu experience :)

---

### Post by riven0 on 2008-04-24
Well, first thing to do is check what wireless card you've got. Most likely it's a Broadcom, which means you'll need the ndiswrapper. But why don't you post the output of these commands:

**lspci**

**iwconfig**

---

### Post by Bannor on 2008-04-24
that one has a broadcom right?  have you been able to revert to the old config?  

What happened to fwcutter? 

I haven't tried this in Hardy but this always worked in the past 

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

I will try it tomorrow and give you an update for hardy.

---

### Post by rob3r on 2008-04-25
Thanks for the replies. I am at work now, but will post the output of those commands when I get back to the house.

Thanks again.

---

