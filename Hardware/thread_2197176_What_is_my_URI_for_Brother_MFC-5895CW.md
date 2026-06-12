---
title: "What is my URI for Brother MFC-5895CW?"
date: 2014-01-02
forum: Hardware
---

### Post by knoticalnate on 2014-01-02
I've been trying to figure out for days how to install my network printer and I think I've figured it out I just need to enter my device's URI.  I have no idea where to get this information and google turns up nothing either.  I've already gone through every available tutorial on the forums and askubuntu and none proved to help my situation.  I just need to know my URI and hopefully everything will be good can anyone assist?  If any other info is needed please let me know.

---

### Post by chili555 on 2014-01-02
Is it attached to another computer on the network or to a port on your router? My printer is attached to my router and works perfectly with:```
ipp://192.168.1.19:631/lp1
```...where 192.168.1.19 is the IP address I reserved for the printer in the router. You may have to play around with 'lp1' or 'lp' etc.

---

### Post by bapoumba on 2014-01-02
Is there a way to print out the network info from the printer itself ? You may find it there.
I had this problem with a HP though, connected via wifi to the router. Once I got the ID, all went smoothly.

---

### Post by knoticalnate on 2014-01-02
> **bapoumba said:**
> Is there a way to print out the network info from the printer itself ? You may find it there.
I had this problem with a HP though, connected via wifi to the router. Once I got the ID, all went smoothly.

The IP on the printer is 192.168.003.106/ I tried putting this in for the URI and it's still unable to connect to the printer.

> **chili555 said:**
> Is it attached to another computer on the  network or to a port on your router? My printer is attached to my router  and works perfectly  with:```
ipp://192.168.1.19:631/lp1
```...where 192.168.1.19 is the  IP address I reserved for the printer in the router. You may have to  play around with 'lp1' or 'lp' etc.

I trieed it as ipp://192.168.003.106/lp and lp1 and it keeps coming up as "Processing - Printer is Busy" when I try to print a test page

---

### Post by chili555 on 2014-01-02
> The IP on the printer is 192.168.003.106/Are you quite sure? Could it be 192.168.3.106? I think you also need the :631 part.```
ipp://192.168.3.106:631/lp
```Perhaps??

Did you follow the process all the way through in System Settings to set the make, model and driver for the printer?

---

### Post by knoticalnate on 2014-01-02
> **chili555 said:**
> Are you quite sure? Could it be 192.168.3.106? I think you also need the :631 part.```
ipp://192.168.3.106:631/lp
```Perhaps??

Did you follow the process all the way through in System Settings to set the make, model and driver for the printer?

Yes I first tried to install it through the system settings but it could not find the drivers for the Brother MFC-5895CW.  I had to manually download the driver and run it as an executable for Ubuntu to install it.  So now it can find the driver at least but it's still not connecting with the any of the URI's I've tried.  I've tried the generic (text only), the URI that it auto assigns it, and all of the above options.  I also tried the 
ipp://192.168.3.106:631/lp and ipp://192.168.3.106/lp ways.  

I'm to the point now where I'm done trying to get it to work.  I have a windows computer at the office I can use to print
I was just trying to do everything in one spot.  No big deal.

---

### Post by chili555 on 2014-01-02
Where did you find the IP address? In the router? Or...?

---

### Post by knoticalnate on 2014-01-02
I found the IP address on the display of the printer itself

---

### Post by chili555 on 2014-01-02
> **knoticalnate said:**
> I found the IP address on the display of the printer itselfHow does that compare to the IP address of other computers on the network?```
ifconfig
```

---

### Post by knoticalnate on 2014-01-02
Lo: inet addr:127.0.0.1  

Wlan0: inet addr:192.168.3.115  Bcast:192.168.3.255  

That's what I get for the IPs

---

### Post by chili555 on 2014-01-02
As you are trying to print, are there any informative messages?```
dmesg | grep -i -e cups -e lpd
cat /var/log/cups/access_log | tail -n5
```

---

