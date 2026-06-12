---
title: "Photobucket website not working (Hardy)"
date: 2008-08-25
forum: General Help
---

### Post by The Barold on 2008-08-25
For the past week I haven't been able to even get into the Photobucket website or see any Photobucket images. I'm using Firefox 3 and Opera 9.52. I have AdBlock Plus plugin for FF3 and I have set it off, added Photobucket to the exceptions list, but even with Opera it wont show and of the images. Anyone having the same problem or know a resolve?

---

### Post by sricketts on 2008-08-25
Do you have flash installed?

-SR-

---

### Post by The Barold on 2008-08-25
Yes I do have flash installed, but that wouldnt stop me from putting the image url and viewing it. "Firefox can't find the server at www.photobucket.com." is the error I get when I try to go to anything with photobucket in it. I've put photobucket in the exceptions for cookies, for loading images automatically also in FF3

---

### Post by The Barold on 2008-09-02
bump

---

### Post by alzie on 2008-09-02
I checked photobucket with no issues at all for me.

I really can't think of a reason for it to not load for you.  Are you able to get into flickr and webshots types of sites?

---

### Post by The Barold on 2008-09-02
Yes, I can get into Flickr and Webshots!:confused:
I really can't get into anything with photobucket in the url.

---

### Post by alzie on 2008-09-02
I'd call my ISP and ask them to go to photobucket.  If they can't its their problem to address.  If they can, maybe they can give you a heads up on where to look.  :confused:

---

### Post by unutbu on 2008-09-02
Try
```

wget http://photobucket.com/
```
If you can download the index.html file, then the problem is in your firefox setup. If you can't download the index.html, then the problem might involve your ISP.

---

### Post by The Barold on 2008-09-02
```
barold@Destro:~$ wget http://photobucket.com/
--17:24:32--  http://photobucket.com/
           => `index.html'
Resolving photobucket.com... failed: Name or service not known.
barold@Destro:~$ ping photobucket.com
ping: unknown host photobucket.com

```
Just got done talking to ISP, maybe its something with my router, but I haven't touched any settings in it. I am gonna try to get another modem seeing as how this one is pretty ancient.

---

### Post by unutbu on 2008-09-02
```
% host photobucket.com
photobucket.com has address 209.17.66.11
photobucket.com has address 209.17.74.21
photobucket.com has address 209.17.70.11
photobucket.com mail is handled by 10 mail.photobucket.com.
```

What happens if you point your browser at [http://209.17.66.11](http://209.17.66.11)

Also, please post 
```

cat /etc/resolv.conf
```

---

### Post by The Barold on 2008-09-03
I can access the url with the ip in it. but once i try to login, it refuses me again.

```
barold@Destro:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5190
#
### END INFO

search consolidated.net


nameserver 192.168.1.1



```

---

### Post by kdwillia on 2008-09-03
It seems like you Router is resolving your domain names instead of using your ISP's DNS.    You might try to change that to the OpenDNS numbers for resolution.   Or, you might just try to reboot your Router and see if that helps the situation.

---

### Post by The Barold on 2008-09-20
Alright, so I got a new modem and plugged directly into the modem and can access the photobucket website. So it definitely has to be my router, but the router I have (Netgear WGR826V) is really bad. And I have looked over and over to see if there is any settings to change, but I havent found any that I would think could. So I guess I can just plug into the modem directly whenever I wanna access the photobucket website. Thanks for the help though.

*would have responded earlier, but I was battling Hurricane Ike

---

