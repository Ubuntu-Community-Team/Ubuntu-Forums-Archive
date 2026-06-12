---
title: "upgrading from 5.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by sqela on 2009-11-06
Ok I'm having one of those Murphy's law days. If it can break it has already. I'm putting back together my Dell Optiplex. only thing working right now besides my hp mini running 9.10 anyway I had several failed attempts to install 9.10 much less anything on my Dell optiplex. two copies of 9.10 and still no luck. I resorted to finding an old shipit copy of 5.10 and installing that to my dell which i'm running now. Now I know its waaaaaaay out of date so is there a way to update it to atleast 9.04? update mananger has told me its no longer supported. ( know and understand) however whats a ubuntu user like myself to do?? My Burner died and the dell bios doesn't support usb stick booting

---

### Post by recluce on 2009-11-06
> **sqela said:**
> Ok I'm having one of those Murphy's law days. If it can break it has already. I'm putting back together my Dell Optiplex. only thing working right now besides my hp mini running 9.10 anyway I had several failed attempts to install 9.10 much less anything on my Dell optiplex. two copies of 9.10 and still no luck. I resorted to finding an old shipit copy of 5.10 and installing that to my dell which i'm running now. Now I know its waaaaaaay out of date so is there a way to update it to atleast 9.04? update mananger has told me its no longer supported. ( know and understand) however whats a ubuntu user like myself to do?? My Burner died and the dell bios doesn't support usb stick booting

Check out this:

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

This should allow you to upgrade to 6.04 LTS. If that works, you can go to 8.04 LTS in one more step. 

Getting to 9.04 would require going through 8.10 first from that point - and I don't know if 4 distribution upgrades in a row would not just be **asking** for trouble.

---

### Post by jollysnowman on 2009-11-06
> **recluce said:**
> Check out this:

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

This should allow you to upgrade to 6.04 LTS. If that works, you can go to 8.04 LTS in one more step. 

Getting to 9.04 would require going through 8.10 first from that point - and I don't know if 4 distribution upgrades in a row would not just be **asking** for trouble.

I agree. Go through all the LTS updates one at a time.

Or perhaps just burn a CD for 8.04?

---

### Post by sqela on 2009-11-06
> **jollysnowman said:**
> I agree. Go through all the LTS updates one at a time.

Or perhaps just burn a CD for 8.04?

Dead burner :(

---

### Post by JugglinPhil on 2009-11-06
> **sqela said:**
> Dead burner :(
Can you not get someone to burn it for you?

---

### Post by sqela on 2009-11-06
> **JugglinPhil said:**
> Can you not get someone to burn it for you?

I asked Mark Shuttleworth but his burner stopped working too

---

### Post by JugglinPhil on 2009-11-06
> **sqela said:**
> I asked Mark Shuttleworth but his burner stopped working too
-.- I was just trying to help..

---

### Post by sqela on 2009-11-06
Wasnt trying to be mean but rather crack a joke about the shipit program. Anyway after some googling and messing with the sources file i think i got it going. I started it then had to leave for some things to do so when i get back ill check if its done

---

### Post by JugglinPhil on 2009-11-06
> **sqela said:**
> Wasnt trying to be mean but rather crack a joke about the shipit program. Anyway after some googling and messing with the sources file i think i got it going. I started it then had to leave for some things to do so when i get back ill check if its done
Alright then, good luck with it.

---

### Post by flipper9 on 2009-11-06
Got a USB Drive/Key?  Then STOP burning discs!  Use unetbootin, install the CDROM ISO to the key, and then boot off the key.  You'll no longer have to pay for CDROM discs, worry about bad burns, and you get a speed boost since USB is faster than reading from a CDROM.

This assumes your computer can boot from a USB drive.

---

### Post by JugglinPhil on 2009-11-06
> **flipper9 said:**
> Got a USB Drive/Key?  Then STOP burning discs!  Use unetbootin, install the CDROM ISO to the key, and then boot off the key.  You'll no longer have to pay for CDROM discs, worry about bad burns, and you get a speed boost since USB is faster than reading from a CDROM.

This assumes your computer can boot from a USB drive.
You should read more carefully, he already said in the original post that he can't boot from usb..

---

### Post by flipper9 on 2009-11-06
> **JugglinPhil said:**
> You should read more carefully, he already said in the original post that he can't boot from usb..
Then I am sorry.  Perhaps get another CDROM drive then?  Goto a friend's house?  Order a copy online? Get a more modern computer?  The possibilities are endless.

Or you can just waste time upgrading, downloading, upgrading again, dealing with upgrade issues, and waste hours of time.

---

### Post by jollysnowman on 2009-11-06
> **flipper9 said:**
> Then I am sorry.  Perhaps get another CDROM drive then?  Goto a friend's house?  Order a copy online? Get a more modern computer?  The possibilities are endless.

Or you can just waste time upgrading, downloading, upgrading again, dealing with upgrade issues, and waste hours of time.

I don't think buying a new computer is really a solution....

---

### Post by JugglinPhil on 2009-11-06
> **flipper9 said:**
> Then I am sorry.  Perhaps get another CDROM drive then?  Goto a friend's house?  Order a copy online? Get a more modern computer?  The possibilities are endless.

Or you can just waste time upgrading, downloading, upgrading again, dealing with upgrade issues, and waste hours of time.
Oh come one, telling someone to get a new computer just because of some problems is ridiculous. Would you get a new car because of a flat tire?

---

### Post by HereSomeHow on 2009-11-06
How about saving the iso's to an usb and mounting them to do the upgrade path from one version to another without burning anything?

---

### Post by louieb on 2009-11-06
Just wondering what CPU, how much ram. How big a hard drive?

I had v5.10 installed and running on a P1-200mHz w/128 MB ram, 3.7GB hard drive.  

Don't know how far you can go with your updates without knowing CPU, ram, and hard drive size.

---

### Post by flipper9 on 2009-11-06
> **jollysnowman said:**
> I don't think buying a new computer is really a solution....
It's a solution.  A better one would be to repair the broken CDROM recorder...amongst the cheapest would be to find a friend to burn it for you instead or borrow a USB CDROM recorder if someone has one.  There are many solutions..but upgrading from an ancient distribution is just asking for trouble.  There are more sensible ways.  Heck...spending hours getting something to work might be worth the $200-$300 you'd spend on a new netbook...get a better computer and save money in the long run.

---

