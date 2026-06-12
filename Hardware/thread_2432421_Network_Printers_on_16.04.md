---
title: "Network Printers on 16.04"
date: 2019-12-02
forum: Hardware
---

### Post by capemayal on 2019-12-02
I have an HP Officejet Pro 8710.  Many have had problems with it.  I have had it working great before.

Now it won''t work.  I have a 2g & 5g networks available.  I'm using static IP.

No matter what I've done, it won't work.  I need both the printing and scanning functions.

Download hplip-3.16.5.  It installs find.  Ran HP-SETUP to no avail.  No HP printer detected.  The HP works 100% on USB.S

I've looked around and found that Penguin has a version of this printer, as well as a Canon ImageClass D570.  I can't get from them the difference between those 2 and the retail versions at Staples, etc.

Does anyone know what separates Penguin from the retailers?  I honestly can't get them to tell me.

I've tried HPLIP from  3.16.5  (min per HP for the 8710) and higher.

Thanks.

---

### Post by SeijiSensei on 2019-12-02
Try visiting [http://localhost:631/admin](http://localhost:631/admin) to get the CUPS administration page then click "Find New Printers." How does that go?

---

### Post by ajgreeny on 2019-12-02
Using hplip-gui you may need to go to the "Show Advanced options" -> "Manual Discovery" and in the box there, enter the IP of the printer.

That has always worked for me if the auto-search does not find the printer.

---

### Post by brian_p on 2019-12-02
You apparently have the device on the network. Execute the command ```
driverless
``` and give us the output.

---

### Post by capemayal on 2019-12-03
> **brian_p said:**
> You apparently have the device on the network. Execute the command ```
driverless
``` and give us the output.

driverless: command not found

The printer goes to sleep after 15 minutes.  That's the max time it can stay awake - in preferences.  There is no provision to turn off the sleep function.

I have emailed Thinkpenquin.  They sell "their" versions of the 8710 and a Canon Imageclass D570.  I asked what's the difference between their printers and the retail versions. I got the same reply twice.  After the 1st one, I asked for a clarification.  That tells me its probably a canned reply.

---

### Post by brian_p on 2019-12-03
> **capemayal said:**
> driverless: command not found

My fault. I forgot you were on 16.04.

How about ```
lpinfo -v
```

---

### Post by capemayal on 2019-12-03
lpinfo -v

network ipps
network ipp14
network beh
network http
network https
direct hp
network ipp
network lpd
network socket
direct hpfax

It appears to me that there isn't anything found.  I've just about given up on this HP printer.

I was able to add the printer through CUPS, but the scanner isn't found.

Thanks for your help though.
Al

---

### Post by brian_p on 2019-12-03
> **capemayal said:**
> lpinfo -v

network ipps
network ipp14
network beh
network http
network https
direct hp
network ipp
network lpd
network socket
direct hpfax

It appears to me that there isn't anything found.  I've just about given up on this HP printer.

No network URI in sight! Very strange considering CUPS allows you to install a queue.

> I was able to add the printer through CUPS, but the scanner isn't found.

There is often a good reason for that. Let us see the result of

```
lpstat -t
```

---

### Post by CatKiller on 2019-12-03
> **capemayal said:**
> I was able to add the printer through CUPS, but the scanner isn't found.

I did find [a report from a Debian user](https://bugs.launchpad.net/hplip/+bug/1728107) that had managed to scan from that device, so perhaps there's some information there that will help you.

---

### Post by capemayal on 2019-12-03
This is after I had installed the printer through cups. No scanner though.

scheduler is running
no system default destination
device for 8710: socket://hostname:9100
8710 accepting requests since Tue 03 Dec 2019 11:10:50 AM EST
printer 8710 is idle.  enabled since Tue 03 Dec 2019 11:10:50 AM EST

After I had deleted the printer through CUPS
scheduler is running
no system default destination
lpstat: No destinations added.
lpstat: No destinations added.
lpstat: No destinations added.
lpstat: No destinations added.

---

### Post by brian_p on 2019-12-03
> **capemayal said:**
> This is after I had installed the printer through cups. No scanner though.

scheduler is running
no system default destination
device for 8710: socket://hostname:9100
8710 accepting requests since Tue 03 Dec 2019 11:10:50 AM EST
printer 8710 is idle.  enabled since Tue 03 Dec 2019 11:10:50 AM EST

The scanner is not automatically discovered because the *device for 8710* (the URI) has to begin with *hp:/net/*. You have *socket://...*.

Not only that, but I would be extremely surprised if you could print with your socket URI; its format is incorrect. What is the IP address for your device?

All of this is easily corrected.

> 
After I had deleted the printer through CUPS
scheduler is running
no system default destination
lpstat: No destinations added.
lpstat: No destinations added.
lpstat: No destinations added.
lpstat: No destinations added.

This is ok.

---

### Post by capemayal on 2019-12-03
Well, Brian, I think I did what you instructed:

lpstat -t =

scheduler is running
no system default destination
device for 8710: hp:/net/192.168.0.130
8710 accepting requests since Tue 03 Dec 2019 04:04:21 PM EST
printer 8710 is idle.  enabled since Tue 03 Dec 2019 04:04:21 PM EST

Still no joy.  Funny thing though, several weeks ago the printer/scanner was working like a charm.  Don't have a clue what happened since then, other than it stopped.  I removed and tried to reinstall.  Then all my problems happened! (:

---

### Post by brian_p on 2019-12-03
> device for 8710: hp:/net/192.168.0.130

This isn't the correct device (URI) either. I bet you cannot print. I'll give you the correct URI and PPD for free. They are

```
hp:/net/hp_officejet_pro_8710?ip=192.168.0.130
```

and

```
drv:///hpcups.drv/hp-officejet_pro_8710.ppd
```

Substitute in

```
lpadmin -p 8710 -v URI -E -m PPD
```

and print with

```
lp -d 8710 /etc/nsswitch.conf
```

How's that?

---

### Post by capemayal on 2019-12-15
Good morning Brian.  Sorry haven't gotten back sooner.

I tried what you suggested, but still can't print/scan.

I'm thinking it has to do with the sleep mode.

I can, naturally, use USB and everything is fine.  But, USB doesn't work from another room.

Thanks again.
Al

---

### Post by brian_p on 2019-12-15
> **capemayal said:**
> Good morning Brian.  Sorry haven't gotten back sooner.

Good evening, Al. No problem.

> I tried what you suggested, but still can't print/scan.

This bothers me quite a bit. I have checked the URI and PPD; there do not appear to be any typos. What do you get for ```
lpstat -v
``` and ```
lpoptions -p 8710
```

> I'm thinking it has to do with the sleep mode.

Pass on this.

---

