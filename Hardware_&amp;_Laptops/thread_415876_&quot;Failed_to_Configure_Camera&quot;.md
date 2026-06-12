---
title: "&quot;Failed to Configure Camera&quot;"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by cwoodworth on 2007-04-20
Hi,
I just installed Feisty, and when I booted for the first time, in hangs for about 30 seconds, then contiunues to load. But then the splash screen disappears, and I get a  lot of error messages about 

```
[  700.168000] ubuntu/media/gspcav1/gspca_core.c: Failed to configure camera usb 5-8: device_add(5-8:1.0) --> -5
```

This message is repeated every second or so. On the left hand side of the error, are some numbers that are increasing in size. [  700.168000]. It's just climbing up. 

My laptop is an Acer 5672 (which has an embedded webcam). It ran Edgy perfectly before.

Any ideas? Thanks a lot.

~Curtis

---

### Post by Vorin on 2007-09-18
i have the same laptop, the same problem.
have you gotten this reselved?
if so, could you help me through it?

---

### Post by Unforsaken92 on 2008-01-27
I am having the same problem with an Acer Travelmate 8200.  The camera never worked but XP didn't freak out about it.  I had Suse for a while and it had the same problem.  Any help would be great.

---

### Post by gukarma on 2008-03-15
Same laptop, same problem...

---

### Post by Diabolis on 2008-03-15
Not really the solution, but Its a start

[https://bugs.launchpad.net/ubuntu/+bug/151684](https://bugs.launchpad.net/ubuntu/+bug/151684)

workaround:

[https://bugs.launchpad.net/ubuntu/+bug/151684/comments/5](https://bugs.launchpad.net/ubuntu/+bug/151684/comments/5)

---

### Post by Trixilver on 2008-05-26
Diabolis, I tried that disable but i got this:

> bash: /etc/modprobe.d/blacklist: Permission denied

I tried "sudo" in front of it, but it still doesn't work.

I tried going to the actual file and adding the code myself but still no luck.

How do I get permission?

---

### Post by Diabolis on 2008-05-26
How you tried to edit the file? you have to add the editor of your preference, so the command would look like this:

```
sudo gedit /etc/modprobe.d/blacklist
```

however this should work:

```
sudo echo "blacklist gspca" >> /etc/modprobe.d/blacklist
```

---

### Post by Chris_Martin on 2008-05-31
Hi there,
I had the same problem and this link really helped:
[https://bugs.launchpad.net/ubuntu/+bug/151684/comments/5]("https://bugs.launchpad.net/ubuntu/+bug/151684/comments/5")
It's mentioned a few posts earlier.
To execute that command from the link I had to change to root, so type

```
sudo -s
```

and enter your password.
Then you can execute this command:

```
echo "blacklist gspca" >> /etc/modprobe.d/blacklist
```

it will add "blacklist gspca" to the file blacklist in /etc/modprobe.d/
after that it wouldn't try to configure the camera.
I use ubuntu 7.10 and have an acer aspire 5670.
I hope it work with you.

---

### Post by Trixilver on 2008-05-31
Thanks guys, I finally got it.

---

### Post by daveappendix on 2008-07-03
I had the same problem, and it turned out to just be loose wiring or something:

[http://ubuntuforums.org/showpost.php?p=5285155&postcount=1022](http://ubuntuforums.org/showpost.php?p=5285155&postcount=1022)

Solution was to flip the camera round and then back again!

Cheers,
Dave

---

