---
title: "no password popup with WPA wifi (atheros)"
date: 2008-11-17
forum: Hardware
---

### Post by deathkill on 2008-11-17
Maybe i don't understand the kde network manager...?

i finally got the Atheros wifi (ath5k) working on an acer aspire a150.

i did so by installing the backports package and disabling the hardware driver for the old ath_pci module leaving the new ath5k one active.

next i 
- click the network manager icon
- click new connection
- choose my wifi router from the detected networks list
- click next
- check "use wireless security"
- choose WPA personal
- leave 'shared key' empty
- click "save and connect"

nothing happens... no password popup or anything
after like 10 seconds the icon goes gray again..

what's suppost to happen? am i doing something wrong or is the driver still not installed correctly??

---

### Post by deathkill on 2008-11-18
hmmz... if i fill in the password in the plaintext area 'shared key' i get a connection.

however,
after like an hour or so the wifi connection failed.
also i can't get any available access points listing anymore..
also a reboot won't help..

seems like my wifi chip died on me... but i find that hard to believe since the laptop is brandnew..

any idea how to get wifi working again?

i read somewhere it supposedly should also work with the ndiswrapper but this solution always gets mentioned as a last resort.. why is this?
anything really bad with ndis wrappers? will it result inarmageddon or cows giving sour milk while wearing silly hats?

---

