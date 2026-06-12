---
title: "Installing a Intel 537 EP modem in Ubuntu 5.10"
date: 2006-02-09
forum: Hardware &amp; Laptops
---

### Post by caven80 on 2006-02-09
Hello People,

Still havnt succeeded in installing my modem drivers on my Ubuntu 5.10.
I ran the scanModem tool n it told me that i hav a Intel based 537 EP modem.

I used the links it provided but to no avail, i couldnt find the drivers for this specific Ubuntu 5.10. (Breezy Badger)

Can someone please tell me from where i can find these drivers and how do i go about installing them.

Thanks n Cheerio!!!!

Caven:cry:

---

### Post by JNowka on 2006-02-10
You have a fun road ahead my friend, I installed the 536ep and it was a pain in the you know what.

Modem Driver:
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9284&strOSs=39&OSFullName=Linux*&lang=eng]("http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9284&strOSs=39&OSFullName=Linux*&lang=eng")

And I would guess that the install is instructions are similar to the ones for the 536ep and you can find those here:
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28537ep%29#head-068a426acfdc8518889ea095253c50b665bce5d4]("https://wiki.ubuntu.com/DialupModemHowto?highlight=%28537ep%29#head-068a426acfdc8518889ea095253c50b665bce5d4")

finally if 537ep is anything like 536ep then you will want to do some editing to a config file.  this is the link to the thread I had:
[http://www.ubuntuforums.org/showthread.php?t=123249]("http://www.ubuntuforums.org/showthread.php?t=123249")

Good Luck

---

### Post by caven80 on 2006-02-10
[QUOTE=JNowka]You have a fun road ahead my friend, I installed the 536ep and it was a pain in the you know what.

Modem Driver:
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9284&strOSs=39&OSFullName=Linux*&lang=eng]("http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9284&strOSs=39&OSFullName=Linux*&lang=eng")

And I would guess that the install is instructions are similar to the ones for the 536ep and you can find those here:
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28537ep%29#head-068a426acfdc8518889ea095253c50b665bce5d4]("https://wiki.ubuntu.com/DialupModemHowto?highlight=%28537ep%29#head-068a426acfdc8518889ea095253c50b665bce5d4")

finally if 537ep is anything like 536ep then you will want to do some editing to a config file.  this is the link to the thread I had:
[http://www.ubuntuforums.org/showthread.php?t=123249]("http://www.ubuntuforums.org/showthread.php?t=123249")

Good Luck[/QUOTE]

Thnks for da Wishes, but i didnt manage to install da modem..
first of all i cudnt find the file Intel537.ko in that zip..
I extracted all da files but cudnt find that  one.
Also i feel the instructions mentioned there are specific to da ones for Intel536.

Please anyone, help me set up my modem on ubuntu..its a Intel537 EP..

Also i am having this issue for not being able to perform task as root
i followed a lead to issue this command 'gksudo nautilus' but it did not work..it asks me for da password but later it doesnt allow me to copy or open any file.

HELP!!!

---

### Post by chuckman78 on 2006-07-09
Hi caven80:

I hope this helps:

[http://www.ubuntuforums.org/showthread.php?t=210405&highlight=537ep]("http://www.ubuntuforums.org/showthread.php?t=210405&highlight=537ep")

Regards,

Carlos.

---

