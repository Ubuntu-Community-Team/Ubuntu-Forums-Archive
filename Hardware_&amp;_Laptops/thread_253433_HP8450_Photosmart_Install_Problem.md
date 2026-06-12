---
title: "HP8450 Photosmart Install Problem"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by mowestusa on 2006-09-08
I know that the HP8450 should work with Ubuntu. It has in the past. I have tried to install under Dapper and I'm having no success at all. I have followed the install instructions on the hplip site, but have not been able to install either. Any suggestions are welcome.

I have it connected to my network and it has an ip of 192.168.1.105.

I have tried connecting through the printer administration gui under system by connecting to ipp://192.168.1.105

I thought that was working, but it is no longer working. I send a print job and it never goes to the printer after waiting several minutes.

Then I read the instructions on the hplip site and followed them exactly using the cups web interface. I first from the CLI got the hp ip number using their utility hp-makeuri. I copied the ip and put it into cups as instructed. Then when I went to make the final install from the web interface. The user name and password for cups was asked for. Being a ubuntu box I don't have a root password. So I put in my user and then my password the same password I use for sudo as well. It would not accept my password which must mean that cups web interface does not like the ubuntu lack of a root user and root password, I'm just guessing.

Not detered I went through the gnome printer dialog and tried to install using the HP Jet Direct connection and put in the special hp uri that I got for the cups web interface. It seemed to install, but when I tried to print a test page I got an error. When I looked at the connection tab it had erased the whole hp uri except for the letters hp when I saved it. I don't understand that either. It did it again when I put in the hp special uri and clicked close.

Any help would be greatly appreciated. I bought this printer because of its strong support under Linux.

mowestusa

---

