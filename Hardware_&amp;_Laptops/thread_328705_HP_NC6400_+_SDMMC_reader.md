---
title: "HP NC6400 + SD/MMC reader"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by opticalfiber on 2006-12-31
I have a business HP laptop nc6400 and it gives, sometimes, problems with its recognization. i read from here hpwiki.cactii.net/hpwiki/NC6400 that I have to add this string (setpci -s 02:06.2 4c.b=02) in startup scripts and i've tried:
sudo echo "setpci -s 02:06.2 4c.b=02" >> /etc/init.d/bootmisc.sh
and it says: access denied  //also if i give the exact password somebody can explain!?:confused: 
the only solution i've found was:
sudo passwd root
//insert a new root password
su -
#echo "setpci -s 02:06.2 4c.b=02" >> /etc/init.d/bootmisc.sh //in this way it's ok!
but i think it's not the exact way..
thx

---

