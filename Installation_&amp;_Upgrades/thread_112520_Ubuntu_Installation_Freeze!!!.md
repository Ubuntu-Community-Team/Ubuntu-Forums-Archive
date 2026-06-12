---
title: "Ubuntu Installation Freeze!!!"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by LebSoLjah on 2006-01-04
hey

I just recieved my copy of ubuntu 5.10. My problem is that everytime i install it,  it freezes at the ''configuring lvm2'' in the base install.. i tried installing it with other install cd`s but i get the same thing. Can someone help me out because it worked fine on my brother`s pc... 

My pc is formatted and the partitions are automatically made. I even tried custom...

Help yould be greatly appreciated...

Thanks

---

### Post by LebSoLjah on 2006-01-05
help ?!?!?!

---

### Post by byen on 2006-01-05
just an off-beat suggestion.
Did you try to install using
acpi-off

usually that seems to be the case.just a suggestion.Goodluck. And welcome to Ubuntu.

---

### Post by LebSoLjah on 2006-01-05
thanks :D

yes i did but no luck... it seems like right after it gets to that part theres no activity... i kept it on for 3 hours but no luck...

---

### Post by byen on 2006-01-05
ok. again..how about this.. can you go to the boot menu and disable legacy support and try it out again.. that did the trick when i was installing suse.

---

### Post by LebSoLjah on 2006-01-05
ill check that out tomorrow and tell u about it right after

talk to u later

---

### Post by LebSoLjah on 2006-01-05
i tried it... still doesn't work

---

### Post by byen on 2006-01-05
ok .was the cd an original cd sent from Ubuntu or did you download it and burn it yourself. If it was downloaded and burned (which i am hoping it is..cause its fixable) Then i would have to say it might be either 
1. corrupt downloaded cd iso
2. it could be a bad cd burn

first after downloading the ISO make sure that yu check the integrity of the ISo by using a program like this:
[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)
(free and secure)
now...after doing this Go to [www.downloads.com](www.downloads.com) and search for the program "deepburner". its free and was developed by the developers with ISO burning in mind. It is really good and damn easy to use. Download it and burn the cd as an ISO project at a slower speed. Let me know if you have any probs. I might have some alternatives.

---

### Post by j_krol on 2006-01-05
I had a similar problem. After trying several other things I checked the pc's memory (using memtest86). It turned out one of the memory sticks was bad.
I took it out and had no problems after that.
Now I have to find the time to try and apply the badram patch  :confused:

---

### Post by LebSoLjah on 2006-01-11
i tested my memory for about 30 hours and no errors were found...

any other solutions?

btw my pc is a dell optiplex gx110

p3 600, 256 ram, 30 gig hd...

---

### Post by LebSoLjah on 2006-01-11
the last lines on the console during install before it freezes...

mprocess /usr/bin/tail -f /var/log/messages (pid 3327) exited. scheduling it for restart

mstarting (pid 30375), console /dev/vc/3:'/usr/bin/tail'

---

### Post by LebSoLjah on 2006-01-12
:confused:

---

### Post by LebSoLjah on 2006-01-12
Wow Thanks For The Help

---

### Post by rutger83 on 2006-01-17
[QUOTE=LebSoLjah]hey

I just recieved my copy of ubuntu 5.10. My problem is that everytime i install it,  it freezes at the ''configuring lvm2'' in the base install.. i tried installing it with other install cd`s but i get the same thing. Can someone help me out because it worked fine on my brother`s pc... 

My pc is formatted and the partitions are automatically made. I even tried custom...

Help yould be greatly appreciated...

Thanks[/QUOTE]


This happened to me when I was trying to boot a non-primary partition. When I re-partitioned it to be primary there wasn't any problem any more. You aren't having any other bugs are you?

---

