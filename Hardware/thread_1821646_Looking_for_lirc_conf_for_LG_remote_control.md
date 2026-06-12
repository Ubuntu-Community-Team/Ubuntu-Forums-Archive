---
title: "Looking for lirc conf for LG remote control?"
date: 2011-08-09
forum: Hardware
---

### Post by honeybear on 2011-08-09
Hello,

Anyone has already irdadump the LG remote controls of current LG monitor? It is easy for all LG today, the remote control is the same. 

I.e. /etc/lirc/hardware.conf?

(I have a LG47LD450 model, so its remote control.) I would like to use this LG to control my mythtv with lirc, but I would be glad to find the conf file... 

Any help welcome

Cheers

My script at boot does:
>   
        killall -e bc567 ;
        cd /etc/lirc ;  ./bc567   -udp  &   
        lircd -n -H udp /etc/lirc/myremotecontrol.conf &

---

### Post by honeybear on 2011-08-09
Then OK, I gotta work on it myself...
1. sudo bc567 -udp -verbose
2. sudo lircd -n -H udp
3. irw


OK. I see already the keys...when I press my LG remote control. let's build it. No one did that already? Come on. there are millions of LG tv in the world ;)

---

