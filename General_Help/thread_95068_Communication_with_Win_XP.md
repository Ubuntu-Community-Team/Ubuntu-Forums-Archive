---
title: "Communication with Win XP"
date: 2005-11-25
forum: General Help
---

### Post by RotR on 2005-11-25
Hello,

I'm a total newbie to ubuntu.

I have 2 PC's, one with ubuntu and one with Windows XP. They are connected using an ethernet crossover cable. The WinXP pc is properly configured for networking (works excellent with the crossover cable with other Win PC's)

My question:
How to get them connected toghether? Do I need the samba thing?

Please help me!

---

### Post by Canuckelhead on 2005-11-25
hey there .. the answer is yes you need the samba thing!  

I have included a link to a great tutorial...  
[http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure]("http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure")

there is so much info in these forums to help you as well... just do a search id that tutorial lets u down.

---

### Post by RotR on 2005-11-25
thank you!

but err... doens't "sudo apt-get install samba" need an internet connection?

that's what I have to install samba for in the first place... ;)

(have got an ADSL modem and well... the eciadsl thing works only for .5 seconds)

can't I put it on USB stick or something?

---

### Post by Bachstelze on 2005-11-25
For me it worked fine without installing anything. Just run System > Administration > Networking. Type your password. Select your Ethernet connection ant click "configure". Check the "Enable this connection" box, select DHCP in the "Configuration" field and click OK. Then try activating your Ethernet connection.

---

### Post by RotR on 2005-11-26
Thank you HymnToLife, your solution worked for me. I'm now on the Ubuntu machine using the crossover cable. But now I want to share a folder on the Ubuntu machine How do I have to do this so that Windows XP can access it?
I want to mention that I have trouble viewing Network Locations on the XP computer. 
Maybe I want to connect to the ubuntu machine by running an FTP server on th ubuntu machine. any ideas?

---

### Post by Bachstelze on 2005-11-26
I haven't tested it myself but I think you should visit the link posted above :) Or if you want to copy something from Ubuntu to XP, you can share a folder with read/write access on your XP machine and then copy your stuff into it from your Ubuntu.

---

### Post by RotR on 2005-11-26
yihaaaaa it WORKS! thank you so much :D

---

