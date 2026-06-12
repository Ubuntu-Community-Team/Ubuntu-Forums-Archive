---
title: "cant update anything on karmic incl. add programs"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by lacrosseperson on 2009-11-03
hi, i seem to be having a real big problem using update manager, synaptic package manager, adding new apps through everything. i had the same problem with 9.10, when i updated from 9.04 to 9.10 using the update manager. so i did a clean install, and still the problem persists. ive got internet, and packages refresh only once i "choose the best server", and this happens on wired and wireless connections. i have also used the main server option. i can download flash, but when it updates the files, it says it has trouble reaching the mirror server. any ideas on how to fix this?

---

### Post by mac9416 on 2009-11-03
Could you post the output of this command?

```
$ sudo apt-get update
```

---

### Post by lacrosseperson on 2009-11-03
here it is

Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic Release.gpg  
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic/main Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic/restricted Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic/universe Translation-en_AU 
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic/multiverse Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic-updates Release.gpg        
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic-updates/main Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic-updates/restricted Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic-updates/universe Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic-updates/multiverse Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic-security Release.gpg
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic-security/main Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic-security/restricted Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic-security/universe Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://mirror.aarnet.edu.au](http://mirror.aarnet.edu.au) karmic-security/multiverse Translation-en_AU
  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Reading package lists... Done
W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic/Release.gpg](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic/Release.gpg)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic/main/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic/restricted/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic/universe/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic/multiverse/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-updates/Release.gpg](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-updates/Release.gpg)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-updates/main/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-updates/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-security/Release.gpg](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-security/Release.gpg)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-security/main/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-security/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-security/restricted/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-security/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-security/universe/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-security/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-security/multiverse/i18n/Translation-en_AU.bz2](http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/karmic-security/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to mirror.aarnet.edu.au:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by D.horse on 2009-11-03
Have you tried just running Update? 

Systems > Admin > Update Manager

I was unable to download or update anything in 9.10 until i ran Update Manager.  Usually it would start automatically but if the computer is running on battery power it does not.

---

### Post by lacrosseperson on 2009-11-03
yeah, that was the first thing i did once i installed 9.10 - still doesnt work to this day

---

### Post by gazo1965 on 2009-11-25
I am having the same problem and get the same output from that sudo update command. 

If I click the Check button in the Update Manager screen, I get a message saying "Updating Cashe, dowloaded 0B of 3B" but the dialog is frozen. 

Any help much appreciated.

---

### Post by lacrosseperson on 2009-11-28
i have a sneaky suspicion it might have something to do with the router settings rather than the computer itself - i can update via a wired connection at work  easily, but at home im getting the the same wired as the wireless (no luck). maybe having a set ip address will have something to do with it?

---

### Post by gazo1965 on 2009-11-29
I think it might have something to do with disabling IPv6 on the router. I have already disabled it in Firefox, so I can browse the web, but maybe I need to either (a) disable IPv6 on the router, and/or (b) upgrade the router firmware. 

I'll give these a try when I can and let you know...

---

### Post by audiomick on 2009-11-29
Hallo.
I take it you are in Australia. That is where your box is trying to get it's updates.

I friend of mine advised me to let the Linux box get it's IP via DCHP. If you set a static one, you have to muck around with routing tables and stuff.

If you want the machine to have a fixed IP at home, try reserving one for it in the router. That works for me.

IPv6 shouldn't make a difference, as it is practically not implemented yet. As far as that goes, you could probably leave it enabled without a worry.

---

### Post by lacrosseperson on 2009-12-01
the problem was the firmware in the router - it just needed to be manually updated. ipv6 doesnt matter. thanks everyone

---

### Post by gazo1965 on 2009-12-03
Yeah, that was my problem too. I eventually upgraded the firmware and got the packages. Hooray!

FWIW I was using a D-link DSL G604T Wireless ADSL router, and you can get the firmware upgrade (and instructions) from the Dlink site or (even better) via your installation CD. 

Make sure you have your ISP details recorded, because you will need to reset the router to factory defaults.

---

