---
title: "werid! harddrive busy all the time!!"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by kakyoism on 2006-12-17
machine: AMD 64
OS: kubuntu 6.06 x86Syndrome: 
Ever since logged in, the harddrive seems to be undergoing a lot of activities (the read/write light is winkling all the time and it sounds pretty much like there are a number of Bit Torrent tasks running, but I didn't run any torrent acts.) even though I'm running just firefox, kate, gaim, and terminal. Looking at the KSystemLog, I got these suspicious messages: 
> 12/17/2006 11:07:46 AM    kakyo-desktop    dhclient    No DHCPOFFERS
> received.
> 
> 12/17/2006 11:07:46 AM    kakyo-desktop    dhclient    No working
> leases in persistent database - sleeping. 
> 
> 12/17/2006 11:10:36 AM    kakyo-desktop    dhclient    DHCPDISCOVER on
> eth0 to 255.255.255.255 port 67 interval 4
> 
> 12/17/2006 11:10:40 AM    kakyo-desktop    dhclient    DHCPDISCOVER on
> eth0 to 255.255.255.255 port 67 interval 11
> 
> 12/17/2006 11:10:51 AM    kakyo-desktop    dhclient    DHCPDISCOVER on
> eth0 to 255.255.255.255 port 67 interval 14 
> 
> 12/17/2006 11:11:05 AM    kakyo-desktop    dhclient    DHCPDISCOVER on
> eth0 to 255.255.255.255 port 67 interval 12
> 
> 12/17/2006 11:11:17 AM    kakyo-desktop    dhclient    DHCPDISCOVER on
> eth0 to 255.255.255.255 port 67 interval 15
> 
> 12/17/2006 11:11:32 AM    kakyo-desktop    dhclient    DHCPDISCOVER on
> eth0 to 255.255.255.255 port 67 interval 5 
> 
> 12/17/2006 11:11:37 AM    kakyo-desktop    dhclient    No DHCPOFFERS
> received.
> 
Do you know if this is the source of my harddrive problem?
Any ideas as to how i'm gonna let my harddrive calm down?
Thanks!

Beinan

---

### Post by taurus on 2006-12-17
How much RAM do you have and do you have any swap partition?

```
free
```

---

### Post by novice_geek on 2006-12-17
First off, please note that i'm pretty new in the Linux world... but...

Just from reading that, I can probably say that you might have a DHCP client running, looking for other machines on the network to give IP addresses and such to.  This doesn't really explain the hard-drive activity, but it's a good thing to look into.
 
Google the name of the app, which is probably "Kakyo-desktop"
 
Do that and see what you get, and close the application if you don't need it.
 
I hope that helps

---

### Post by kakyoism on 2006-12-17
To taurus:

I got 1G RAM, 1G swap as a standalone partition, and note that
this problem didn't happen last time I was using it, a week ago.
I didn't add anything new to the system.

And the ps command doesn't show any suspicious processes running.

Thanks!

---

### Post by kakyoism on 2006-12-17
to novice_geek,
thanks for your answer, i didn't get any result from the google search.
but just wanna know if the DHCP is a big problem for me, because i don't 
have a problem doing regular tasks such as webbrowsing but did fail to 
remote-desktop to my machine from elsewhere.

thanks.

---

### Post by taurus on 2006-12-17
> **kakyoism said:**
> To taurus:

I got 1G RAM, 1G swap as a standalone partition, and note that
this problem didn't happen last time I was using it, a week ago.
I didn't add anything new to the system.

And the ps command doesn't show any suspicious processes running.

Thanks!

And both your RAM and swap aren't maxed out!

```
free
```

---

### Post by kakyoism on 2006-12-17
I don't think so. It can't be maxed out with such few apps running...

---

### Post by taurus on 2006-12-17
But have you looked at the output of that command???

```
free
```

---

### Post by kakyoism on 2006-12-18
oh, sorrry,
i was too careless to notice that 
code: free means a command!!
I thought it was your signature or sth.

I'll look at it and get back here!
(i'm on windows right now because of the problem...)

---

### Post by kakyoism on 2006-12-18
Below is the output of "free":

             total       used       free     shared    buffers     cached
Mem:       1035080     448036     587044          0      21152     257372
-/+ buffers/cache:     169512     865568
Swap:      1052216          0    1052216

shoot, as I pasted here, the harddrive starts rambling again although it has been quiet for a minute when just logged in.

---

### Post by taurus on 2006-12-18
Run the **top** command from a terminal to see which program is accessing your harddrive!

---

