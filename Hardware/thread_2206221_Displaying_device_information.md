---
title: "Displaying device information"
date: 2014-02-18
forum: Hardware
---

### Post by GAURAV_PANT on 2014-02-18
Hi,am trying to list all the scsi disks connected and display their information.In windows i have used setupapi class for doing the same.So can u suggest any alternative way or setupapi equivalent in ubuntu.I am using ubuntu 12.10.

---

### Post by mörgæs on 2014-02-18
Hi, welcome to the fora.

You can try 
```
sudo lshw -sanitize > lshw.txt
```

---

### Post by GAURAV_PANT on 2014-02-18
[COLOR=#DD4814][COLOR=#C61919]thanx [mörgæs]("http://ubuntuforums.org/member.php?u=939075")[/COLOR][/COLOR][COLOR=#000000]  
actually am searching for an API. 

[/COLOR]

---

