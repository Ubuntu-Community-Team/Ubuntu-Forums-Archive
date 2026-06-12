---
title: "Trying to upgrade from 6.06 to 7.04 - think all Edgy update packages have been moved"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by chrisgeller on 2009-03-22
Hi

I'm trying to upgrade from 6.06 to 7.04. When I try to do this through update manager, it tells me

"Error during update A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry."

It then lists the Edgy packages it's failed to find on the network - manually typing these into the URL bar shows they aren't actually there on the server.

They are:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz) 404 Not Found


What do I do to upgrade?

I'm eventually trying to upgrade to 8.10.

---

### Post by tommcd on 2009-03-22
Edgy is no longer supported, and the repos no longer exist. You can verify this by checking the mirror you are using:
[http://gb.archive.ubuntu.com/ubuntu/dists/](http://gb.archive.ubuntu.com/ubuntu/dists/)
I would recommend doing a clean install of Ubuntu Intrepid 8.10. Then you can upgrade to Jaunty 9.04 when it comes out next month.

---

### Post by chrisgeller on 2009-03-22
Thanks - unfortunately that's a bit of a nightmare - my computer is too old to boot from USB and I'm all out of writeable CDs :(

Is there anyway I can upgrade from within 6.06 or Windows? I've tried messing around with the source list, but think I'm just making things worse

---

### Post by theozzlives on 2009-03-22
7.04 has reached end of life also

---

### Post by Sef on 2009-03-22
>  I'm trying to upgrade from 6.06 to 7.04. When I try to do this through update manager, it tells me

Upgrade to Hardy Heron (8/04.)  You can upgrade directly to it from Dapper Duck (6/06.)

---

### Post by flyingfree on 2009-03-22
I have tried this route but the upgrade did something to my network connections andwhen i put heron on my system my mnetwrok connectons drops and freezes the whole system when I do anyhting bandwidth intense, ie synaptic packages, video files, etc...If edgy is gone I take it fiesty is to. supposeddly with the rt61 chip fiesty was the last one to have it working well.
Any way to go from dapper to fiesty, or maybe gutsy?  I don't want to install 8/04 again, as it was what caused the network problem.  Lot of synaptics and upgrades in dapper with no problems yet.  Clean install of intrepdi didn't work either.

---

### Post by tommcd on 2009-03-22
> **chrisgeller said:**
> 
Is there anyway I can upgrade from within 6.06 or Windows? I've tried messing around with the source list, but think I'm just making things worse
Since 6.06 was a LTS (long term support) version, you can upgrade directly from 6.06 to 8.04 LTS. After verifying that the upgrade to 8.04 worked ok, you could then consider upgrading from 8.04 to 8.10. See this:
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)
Please put your sources.list back to the way it was with the official Dapper repos first to avoid problems.

EDIT: I didn't see Sef's post or your last post before I posted this.
I also use the rt61 wireless driver. For me it worked straight out of the box in Hardy with no problems. It is likely that something else may be locking up your system.

---

### Post by chrisgeller on 2009-03-23
> **Sef said:**
> Upgrade to Hardy Heron (8/04.)  You can upgrade directly to it from Dapper Duck (6/06.)

Hi - when I go to up ate manager I'm only offered 7.04 - how do I go straight to 8.04?

---

### Post by lisati on 2009-03-23
> **theozzlives said:**
> 7.04 has reached end of life also

True: and 7.04 is "Feisty", not "Edgy"

---

### Post by tommcd on 2009-03-23
> **chrisgeller said:**
> Hi - when I go to up ate manager I'm only offered 7.04 - how do I go straight to 8.04?

Did you follow the link I gave in my last post? Update amanger should offer you the option to upgrade to 8.04.

---

