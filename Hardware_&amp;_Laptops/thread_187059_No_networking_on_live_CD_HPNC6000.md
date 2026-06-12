---
title: "No networking on live CD HPNC6000"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by dshuck on 2006-06-02
I am completely new to Ubuntu and decided to give it a try on my NC6000.  I decided to test the live CD before commiting, and everything seems to be behaving as I would expect it to except for networking.  I cannot lease a DHCP address, and if I hardcode the address I cannot access other systems.  Is there something obvious about using Ubuntu on an HP NC6000 that I should know?  Thanks in advance.

---

### Post by CitizenKane on 2006-06-02
I have something that you can try out.  I don't know if you are new to linux, but it does include command line stuff.  Don't worry, it isn't too hard.  Alright, first off go to the gnome menu in the top left corner (it says Applications).  Then go to Accessories --> Terminal.

Once that gets open type (or copy paste) the following and make sure that an ethernet cable is plugged into the network slot.

```

sudo dhclient

```

If your router is working you should see an IP address come up.  If you are still having problems message back.

---

### Post by dshuck on 2006-06-05
Well that is just awesome!

So, to help me get my head around this... if the OS was actually installed, would the process that runs to get the DHCP address have had the proper rights without me having to do 'sudo'?  Is this something that I will have to manually do even in a standard installation?

Thanks for you input CitizenKane.

---

