---
title: "problem connecting to internet"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by umairsaeed219 on 2007-06-23
i have intel 536ep modem
i have successfully installed it by using step by step guide on **DialupModemHowto/Intel536EP **
everything went smoothly as mentioned in guide 
 
in this guide section using the modem state 
Using the modem

    *

      The name of your modem device is /dev/536ep0. You can now use

sudo pppconfig to set up pon & poff. To use Kppp you will need to create a symlink be able to link the /dev/536ep0 to /dev/modem. Udev rewrites the /dev on each reboot and you thus have to create a file /etc/udev/rules.d/10-local.rules and put the following lines in it:

    *

        # Intelmodem536ep
        KERNEL=="536ep0", SYMLINK=="modem"

so i have tried pppconfig (i think kppp is not prest in ubuntu 7.04 it is kubuntu   )
results produced by plog is 

$ pon    # connect to the ISP configured as "provider"
pppd[5836]:ppd 2.4.4 started by umair ,uid 1000
          :abort on (busy)
                    (no carrier)
                    (no voice)
                    (no dial tone)
                    (no answer)
                    (delayed)
           :send ATZ^M
            expect (0        





later on when i tried again 

plog produced 
pppd[5836]:ppd 2.4.4 started by umair ,uid 1000
device ttyS0 is locke by pid 5836 
exit

---

### Post by Sepero on 2007-09-12
Ever get that working? I think Not. At the end of the guide it says pppconfig does Not work with 536ep modems. ( I wrote that :) )

You need to use wvdial or gnome-ppp.

---

