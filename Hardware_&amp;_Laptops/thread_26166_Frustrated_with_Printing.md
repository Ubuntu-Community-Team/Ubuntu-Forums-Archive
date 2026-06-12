---
title: "Frustrated with Printing"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by exphiles on 2005-04-12
I've been using Ubuntu for about a week now and I really like it. Unfortunately, I'm beginning to get really frustrated because I can't get printing to work.

I have an XP machine where my HP5510 All in one printer is connected. I can print fine when I boot with XP on my laptop but I can't print when I have Ubuntu running.

I don't get it. I can browse and transfer files from my XP box to Ubuntu fine with Samba. But how come I can't print? I think I already set it up properly. With regards to the printer driver, I know my printer is supported in linux.

When I print, the printer starts a bit but pauses and never continues. When I look at the spool manager in XP. I see 64.0K of 7Mb. But it's stuck there.

I've also configured CUPS and enabled root password to run the [http://localhost:631](http://localhost:631) but I get the same problem.

Does anyone have any solutions to this? I remember that when I had Suse 9.2 installed I was able to print fine. I'm beginning to consider changing my distro just to get this printing to work. It's putting a hold to my transition to linux.

 :mad:

---

### Post by orion_114 on 2005-04-12
Try this thread ....
[http://www.ubuntuforums.org/showthread.php?p=124137](http://www.ubuntuforums.org/showthread.php?p=124137)

---

### Post by exphiles on 2005-04-13
Thanks for the help Orion. I already saw that thread before I posted and I still haven't gotten my printer to work.



[QUOTE=orion_114]Try this thread ....
[http://www.ubuntuforums.org/showthread.php?p=124137](http://www.ubuntuforums.org/showthread.php?p=124137)[/QUOTE]

---

### Post by Dogmeat on 2005-06-13
That happened to me when I changed some network names and stuff. I had a hard time getting it to work, and I had the exact same problem. Here's what I did:

1 - Delete your network printer in Ubuntu

2 - Create it again (as SMB printer) put your XP machine's IP, shared printer's name, and user as 'guest'. Leave password blank.

3 - Select your printer's driver, and make sure the printer is shared, try disabling your firewall on XP and on ubuntu for this test. 

4 - Don't change anything in printer properties. The username will be blank, and there will be ***** where the password is. Leave that alone, for some reason changing it doesnt work.

5 - Print away  ;-) 

6 - If step 5 fails, check /var/log/cups/error_log and post it here

---

### Post by Lu523 on 2005-09-23
Thanks for the tip. It worked great.

---

### Post by bucket on 2007-02-14
I had a similar issue but this didn't fix it.  Mine was stalling at 64.0kb/print size job in windows

 FIX -- In windowsXP , right click printer, Properties, Advanced, Ports and DESELECT "Enabled bidirectional support"..

 it'll stop clicking and whirring and print properly.

---

