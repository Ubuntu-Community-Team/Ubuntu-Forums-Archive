---
title: "ATI Radeon hd3850 graphics problem!!"
date: 2010-02-06
forum: Hardware
---

### Post by Furetgarcon on 2010-02-06
I have an dell optiplex with and pci-e hd radeon 3850 installed in . with the card installed i get no video with the card out of the machine i do get video. I am able to blindly login with the card installed but i cant see anything because there is no video. I need a answer soon.

---

### Post by derekmbarnes on 2010-02-07
Probably needs the FGLRX acceleration driver. I don't quite remember where to get it, but if there's no ATI-built driver in the system then it's probably not going to run.

---

### Post by Furetgarcon on 2010-02-07
I have installed the ati drivers i got from the ati website  and still nothing...

---

### Post by Furetgarcon on 2010-02-07
> **derekmbarnes said:**
> Probably needs the FGLRX acceleration driver. I don't quite remember where to get it, but if there's no ATI-built driver in the system then it's probably not going to run.
 I have reinstalled the drivers and  i placed in the card and im stilling getting a black screen......

---

### Post by Furetgarcon on 2010-02-07
Anybody out there?!?........... :sad:

---

### Post by Kenny_Strawn on 2010-02-07
Have you tried disabling Compiz? Or is it enabled at all?

---

### Post by lorddaddy84 on 2010-02-08
Add this line to boot options, "pci=use_crs" without quotes. May not work for you, but did for me. My graphics card is similar.

---

### Post by Furetgarcon on 2010-02-08
> **Kenny_Strawn said:**
> Have you tried disabling Compiz? Or is it enabled at all?
No compiz  the problem only happens when the card is installed so for me to use the crappy intel graphics compiz must be off .... :icon_frown: I have no clue what to do anymore.

---

### Post by tekkidd on 2010-02-08
ATI good luck

---

### Post by Furetgarcon on 2010-02-08
> **lorddaddy84 said:**
> Add this line to boot options, "pci=use_crs" without quotes. May not work for you, but did for me. My graphics card is similar.
Hmmm how would i do that :-k Im an total N00B #-o

---

### Post by Furetgarcon on 2010-02-08
I dont know if this helps but i found out  the blank screen is actually just no video. I was able to login blindly*which didn't help considering all i could see is black! ](*,)* I Still dont know what to do :?

---

### Post by Furetgarcon on 2010-02-14
:sad: anybody?

---

### Post by WSmart on 2010-03-09
Just be glad you don't have the AGP version.

And what this sounds like to me is your display is not getting picked up correctly.  I have an old display and have to add vertrefresh and horizsync to the /etc/X11/xorg.conf in order for the display to work correctly.  

I suggest you search online with your display model as one of the key terms and see what comes up.

---

### Post by adam814 on 2010-03-09
The problem with the drivers from the ATI website is they're held back to support "Enterprise" Linux.  They work fine on just about any Ubuntu Intrepid and older (including Hardy of course).  As long as RHEL and SLED are still using 2.6.18 or some similarly old kernel I wouldn't expect much support for anything newer than Intrepid (which uses a 2.6.27 series kernel I believe).

So basically for newer versions you'll have to get by with the open-source radeon driver.  I have an HD 3470 that works OK with it in Lucid Alpha 3.  The hardware 3D isn't the fastest performer, but it works as well as compiz.

---

