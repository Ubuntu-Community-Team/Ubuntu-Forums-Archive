---
title: "z-star webcam"
date: 2008-05-05
forum: Hardware
---

### Post by benquick on 2008-05-05
my cheap webcam doesn't work
a had a downloading the driver from [http://mxhaard.free.fr/download.htm]("http://mxhaard.free.fr/download.html")l, and install it on my computer
```

bokura@bokura:~$ lsusb
Bus 003 Device 010: ID 0ac8:307b Z-Star Microelectronics Corp. 
Bus 003 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```
and inserting module gspca
```

sudo modprobe gspca
```
camorama can detecting my webcam but no picture, its seem like freeze and camorama going not responding 
i try to change the permission
```

sudo chmod 777 /dev/video0
bokura@bokura:~$ ls -l /dev/video0
crwxrwxrwx 1 root video 81, 0 2008-05-05 18:37 /dev/video0

```
but problem doesn't resolved
I try my webcam on hardy (I check gspca is in the repository and install it), same as in my gutsy computer
here the screenshot 
[IMG]http://i286.photobucket.com/albums/ll89/belutnakal/camorama.png[/IMG]
now I need to buy a new webcam, and I need to know what a good webcam that support ubuntu, except anyone can resolve my webcam problem

---

### Post by aikiwolfie on 2008-05-05
Have you installed cheese?

sudo apt-get install cheese

---

### Post by benquick on 2008-05-05
```

Have you installed cheese?

```
Yes i did, cheese, camorama, and easycam had installed on my computer, any idea?

---

### Post by benquick on 2008-05-07
anyone can help me, please
or what webcam support for ubuntu? anyone know? i need to buying a new camera but i don't wanna this problem happen again.....

---

### Post by erginemr on 2008-05-07
Probably, I am not the one to advise, because I couldn't have my crappy webcam to work in Ubuntu (which is not Ubuntu's fault), but can you please try installing **easycam** or **easycam2** from:
[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

to check whether it will detect your webcam? It didn't detect mine, but I hope you will be luckier...

---

### Post by benquick on 2008-05-08
erginemr, thank's for reply
```

Probably, I am not the one to advise, because I couldn't have my crappy webcam to work in Ubuntu (which is not Ubuntu's fault), but can you please try installing easycam or easycam2
```

easycam/2 was installed on my gutsy and hardy before you give me suggestion:confused:

---

### Post by erginemr on 2008-05-08
Sorry for that. If your attempts proove unsuccessful and you decide to purchase another webcam, you can take this shopping list with you:
[http://isabel.dit.upm.es/content/view/50/2/](http://isabel.dit.upm.es/content/view/50/2/)
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

According to this list, mostly Logitech, and to some extent, Creative webcams are supported under Linux.

---

### Post by benquick on 2008-05-08
Erginemr, thank's for your information
i'am going to that page

cheers, Ben

---

