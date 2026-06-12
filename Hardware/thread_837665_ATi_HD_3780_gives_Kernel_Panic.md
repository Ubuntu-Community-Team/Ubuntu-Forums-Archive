---
title: "ATi HD 3780 gives Kernel Panic"
date: 2008-06-22
forum: Hardware
---

### Post by HansKisaragi on 2008-06-22
I know there is a lot of people who have this problem .. but iv never found a solution for this..

Every time i install the ATi Restricted drivers .. with EnvyNg or from The restricted driver tool itself.

After an hour or two .. i get Kernel Panic, everything freezes.. keyboard leds flashing and i have to shutdown.

Iv tried Hardy 8.04 and the latest Linux Mint.

It all started after i changed my old nvidia card to a new ATI HD 3780.

I was forced to format back to windows today cause it kept freezing constantly.

So if somebody could point me to a guide or tell me what to do, i would be very happy.

Thanks in advance,


-update- 

I forgot to mention that i added 2 extra gig ram after i upgraded to 8.04 .. from 2 to 4 gig.

they are all same hz and type

---

### Post by angryfirelord on 2008-06-22
The driver in the repositories might be too old. Try using the newest driver instead: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29")

---

### Post by HansKisaragi on 2008-06-22
Okey, will try them and report back,

Thanks

-update-

Okey so far it seems good .. *crosses fingers*

viiral@hatenkou:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3870
OpenGL version string: 2.1.7659 Release

---

### Post by HansKisaragi on 2008-06-27
Bah .. It did not solve my problem .. i got another kernel panic after a few hrs .. :(

-update- 

I forgot to mention that i added 2 extra gig ram after i upgraded to 8.04 .. from 2 to 4 gig.

they are all same hz and type

---

