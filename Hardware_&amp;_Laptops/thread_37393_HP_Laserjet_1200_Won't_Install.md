---
title: "HP Laserjet 1200 Won't Install"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by palsyboy on 2005-05-27
I just moved over to Kubuntu after a year of SuSE and Gentoo.  For the life of me, I can't figure out how to get my HP Laserjet 1200 installed on my machine.  I'm used to setting up CUPS via my browser, but I get the following message: "Administrative tasks have been disabled for security reasons. Please use Menu System > Administration > Printing."  I've tried using root + root's password to log in, and I've used my normal username and password, but I get rejected every time.

I've tried setting up my printer via KDE's Control Center, and it leads nowhere.  I'm asked to press "OK" after the printer has finished printing, but nothing happens.

Can anyone point me in the right direction here?  Thanks.

---

### Post by jjross on 2005-05-27
I am having the same problem with an hp psc950. I am getting the same messages as you are,password wont work etc. I really hope someone has an answer for this

---

### Post by palsyboy on 2005-05-29
Well, I happily got it fixed.  What I had to do was add my normal user back to the sudo group.  I had previously emptied the sudo group of all users, as I greatly prefer to su to root.  I just had to run kuser as root from a terminal, and then Control Center printed a test page from my printer.

Perhaps this is the same problem you're having, jjross?

---

