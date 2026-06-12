---
title: "installing google earth"
date: 2008-10-15
forum: General Help
---

### Post by moondogie on 2008-10-15
Can I get some help using the command line after downloading google earth to my desktop to install google earth .
I have downloaded the program to my desktop and gone to the google site and followed directions on how to install to no avail. I am running version 8.04 .
Thanks Marty

---

### Post by Sam on 2008-10-15
You'd better add the [Medibuntu repository](https://help.ubuntu.com/community/Medibuntu), then install the package [googleearth](apt://googleearth).

---

### Post by oldos2er on 2008-10-15
> **moondogie said:**
> Can I get some help using the command line after downloading google earth to my desktop to install google earth .
I have downloaded the program to my desktop and gone to the google site and followed directions on how to install to no avail. I am running version 8.04 .
Thanks Marty

 Open a terminal and enter these commands one at a time:

cd Desktop

chmod a+x GoogleEarthLinux.bin

sudo ./GoogleEarthLinux.bin

---

### Post by moondogie on 2008-10-15
> **Sam said:**
> You'd better add the [Medibuntu repository](https://help.ubuntu.com/community/Medibuntu), then install the package [google-earth](apt://google-earth).

THanks , That did the trick . Medibuntu is happening for the extra programs available .
Marty

---

### Post by moondogie on 2008-10-15
> **oldos2er said:**
> Open a terminal and enter these commands one at a time:

cd Desktop

chmod a+x GoogleEarthLinux.bin

sudo ./GoogleEarthLinux.bin

Thanks Ann ,
I installed the Medibuntu package and then installed GE from there .

I really appreciate the help everyone shares with Ubuntu 
Marty

---

### Post by jimjutte on 2008-10-21
Hi Ann,

Your assistance was nice and simple. I was also able to use your instructions to install Adobe Air :)

Cheers
Jim

---

