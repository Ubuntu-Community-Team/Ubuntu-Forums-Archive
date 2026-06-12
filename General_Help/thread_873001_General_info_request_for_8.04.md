---
title: "General info request for 8.04"
date: 2008-07-28
forum: General Help
---

### Post by jbb on 2008-07-28
I currently run Ubuntu 7.10 on a Acer 3620 laptop with 2gB RAM . I use a HUAWEI 220E to connect to internet and am relatively new to Linux  being an old time DOS/Windows user 

1.  Virtualisation   How does a newbe use this new inbuilt feature?  Need to be able to have virtual copy XP 

2.  Although I fiqured out how to get my modem (a Huawei 220 ) to work on Ubuntu 7.1  ( see my HOWTO in the absolute beginners section ) I was unable to get it to work on Ubuntu 8.04 even using the methode I described above.
( yet it worked 1st time on a live Mandriva 2008.1 DVD -  Mandriva saw the device and set it up then connected )  My HOWTO explained connecting a Huawei 220 using the Vodafone connect card driver and downloading ~10 python files in a specific order. If this combo worked on 7.10  why doesn't it work on 8.04?

3. Wammu   what is required to get it to work on ubuntu 8.04?

Many thanks

JBB

---

### Post by coffeecat on 2008-07-28
I can only offer an opinion on question 1. I have no experience of the other two.

As far as virtualisation is concerned, I can recommend VirtualBox. I use the MacOS version on my Mac Mini and I have successfully virtualised Ubuntu, Zenworks and openSUSE11 in it. They all work fine. I haven't tried Windows as a guest OS, but from what I've read it should be fine, and should be fine with a Linux host. The only problem I've come across with running Ubuntu virtualised in MacOS is that the default Ubuntu desktop clashes horribly with the Leopard desktop. :wink: Orange-brown and Purple-Blue. Eeeoouw.

However - I see that the version of VirtualBox in the repository for Hardy is 1.5.6, which you don't want to install. If you want to give it a try, I suggest you go to [http://www.virtualbox.org/](http://www.virtualbox.org/) where you can get the latest 1.6.2 version. [This page]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter;pgid=01RgaHqkAdxSR0EUQncsoQ3D0000HWHlbm3-;sid=LTgQ84kpYtQQ9sGnN4JY9maP4oJlekRseNrfMpQ302p_5w==") * gives you the .deb installation file for 32-bit Ubuntu 8.04. If you want the 64-bit version, you can navigate from the home page. While you're at the VirtualBox website, don't forget to download the pdf for the manual. It's very clearly written and you do need to read it before starting.

Others may recommend VMWare. I have no experience of it.

* **Edit**: Whoops! There's a licence agreement to sign before that page. It doesn't like being linked to. Go to [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI) and select your platform and agree to the licence. You should then be able to download the .deb.

---

### Post by jbb on 2008-07-30
Thanks for an interesting reply.:)   I am looking for help in migrating from Ubuntu 7.1 to Ubuntu 8.o4 but don't wish to burn my bridges. I need to be able to download whatever files I need for this using 7.10 before going whole hog and installing 8.04.  Hopefully this way I will meet less hassles getting online and setting up a virtual XP system (need for PLC programing  :( unfortunately) 
Any help would be appreciated

---

