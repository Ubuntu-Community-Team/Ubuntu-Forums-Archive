---
title: "Package Manager woes"
date: 2008-07-31
forum: General Help
---

### Post by renegadeandy on 2008-07-31
Hi!

Im not sure how this happened but I have been trying to get ICS working with my xbox for a little while and I did some editting etc from the forum guides around here with ipmasq dnsmasq etc and have since removed these 2 programs and tried to revert all changes.

However when i login using the gui to ubuntu - it hangs for about 5 minutes before an error message appears stating that the gui demon or something couldnt be started , probably due to a firewall rule or something. Then when i try to install packages such as firestarter by doing - 

sudo apt-get install firestarter, it downloads, then when installing it says:
```

Firewall script saved as /etc/firestarter/firewall
Adding Firestarter startup hook to /etc/dhclient-exit-hooks
 * Stopping the Firestarter firewall...                                  [ OK ] 
 * Starting the Firestarter firewall...                                  [fail] 
invoke-rc.d: initscript firestarter, action "restart" failed.

```

When i try to restart it just fails again!

Help help help! Everything is falling apart :lolflag:

---

### Post by Archimedes0212 on 2008-07-31
have you tried installing firestarter through the Add/Remove Programs section??

---

### Post by bodhi.zazen on 2008-07-31
Firestarter is depreciated and I have seen problems with it, especially if you have more complex firewall needs.

I think you should remove (purge) firestarter and use UFW.

```
sudo apt-get remove --purge firestarter
```

UFW is command line only, although I am sure we will see gui tools, but it is easy to use and superior to Firestarter.

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

GUI : [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

I have not tried gufw ...

---

