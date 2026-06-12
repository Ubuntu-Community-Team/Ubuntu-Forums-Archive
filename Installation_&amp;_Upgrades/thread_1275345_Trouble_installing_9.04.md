---
title: "Trouble installing 9.04"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by Bunny Boy on 2009-09-25
I want to do a fresh install of 9.04 on a computer that has successfully run 6.06 for over three years.  

Problems so far:  

1.  The install disk does not recognize my graphics card or monitor, so will only run in low-res mode.  

2.  There appears to be no support for dial-up modems.  The help text says: 

 "NetworkManager doesn't currently support modem connections, so you will need to install the gnome-network-admin package.  If you have no working Internet connection, then you will need to obtain this package and install it, see Downloading and installing a .deb package for more information."  

OK, so to get on the internet with your modem, first you have to get on the internet and download this program to support your modem!  Well, since I discovered this before I took the leap, here I am on the internet still using my old OS, but when I look in synaptic I don't see any package called "gnome-network-admin"!!

Any ideas?  I'm more than a little miffed that Ubuntu seems to be abandoning 10% of the population.

---

### Post by Jazzy_Jeff on 2009-09-25
Google is your friend. You can download from the bottom of this link. [http://packages.ubuntu.com/intrepid/gnome-network-admin](http://packages.ubuntu.com/intrepid/gnome-network-admin) 

As for Ubuntu abandoning 10% of the population, they are not. They have to pick and choose what goes on their live CD's since they have a limited amount of space to work with. As you can see the package is easily obtainable with a quick Google search.

---

### Post by Bunny Boy on 2009-09-26
> **Jazzy_Jeff said:**
> Google is your friend. You can download from the bottom of this link. [http://packages.ubuntu.com/intrepid/gnome-network-admin](http://packages.ubuntu.com/intrepid/gnome-network-admin) 

As for Ubuntu abandoning 10% of the population, they are not. They have to pick and choose what goes on their live CD's since they have a limited amount of space to work with. As you can see the package is easily obtainable with a quick Google search.

I can't say I agree.  For anyone starting from scratch with only dial-up access available, it certainly is not "easily obtainable"!  It's a little hard to swallow that dial-up takes up so much space!

What about the video resolution?  Why is it that 6.06 can handle my hardware but 9.04 can't?  Is there a package that will run the gamut of video configurations?

---

### Post by Jazzy_Jeff on 2009-09-26
> **Bunny Boy said:**
> I can't say I agree.  For anyone starting from scratch with only dial-up access available, it certainly is not "easily obtainable"!  It's a little hard to swallow that dial-up takes up so much space!

What about the video resolution?  Why is it that 6.06 can handle my hardware but 9.04 can't?  Is there a package that will run the gamut of video configurations?

Video is another issue all together. I am assuming you are either using a ATI card or intel. ATI stopped supporting a lot of their older cards. Not sure about the intel problem since I have not checked into it myself. I only use nvidia cards now.

---

### Post by Bunny Boy on 2009-09-27
> **Jazzy_Jeff said:**
> Video is another issue all together. I am assuming you are either using a ATI card or intel. ATI stopped supporting a lot of their older cards. Not sure about the intel problem since I have not checked into it myself. I only use nvidia cards now.

This is what lspci tells me:

*VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChr ome] Integrated Video (rev 01)*

How does that help me when I install 9.04?

---

### Post by DFlame on 2009-09-27
Have you tried Hardy (8.04) at all? It may be better to go from one LTS release to another.

---

### Post by Bunny Boy on 2009-09-28
> **DFlame said:**
> Have you tried Hardy (8.04) at all? It may be better to go from one LTS release to another.

I'm doing a clean install! I don't see how that's an issue.

---

